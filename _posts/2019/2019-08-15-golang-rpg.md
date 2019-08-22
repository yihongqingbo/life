---
layout:     post
title:     http tcp rpc socket
no-post-nav: true
category: golang
tags: [golang]
excerpt: 指针符号 * 和 &
---
### HTTP TCP RPC gRPC socket都是啥
* tcp 是传输层协议，解决数据如何在网络中传输，以二进制数据流的形式传输。对开发不友好
* http 是应用层协议 建立在tcp协议之上的应用，解决如何包装数据。对开发友好
* socket 是针对tcp udp的具体接口实现
* rpc 远程过程调用，a服务器调用b服务器上的方法
* gRPC是一个rpc框架
### 有http为啥还要有RPC
PRC不基于网络，在分布式机器上调用和本地调用差不多。协议私密安全效率高

### go rpc  demo

服务端

```golang
package main
type Args struct{
	A ,B int
}
type Quotient struct{
	Quo,Rem int
}
type Arith int

//计算乘机
func (t *Arith) Multiply(args *Args,reply *int) error{
	time.Sleep(time.Second*3)
	*reply =args.A * args.B
	return nil
}
func (t *Arith) Divide(args *Args,quo *Quotient) error{
	time.Sleep(time.Second*3)
	if args.B == 0{
		return errors.New("divide by zero")
	}
	quo.Quo = args.A / args.B
	quo.Rem = args.A % args.B
	return nil
}
func main(){
	//创建对象
	arith := new(Arith)
	//rpc服务注册了一个arithd对象 公开方法供客户端调用
	rpc.Register(arith)
	//指定rpc的传输协议 这里采用http协议作为rpc调用的载体
	rpc.HandleHTTP()
	l,e :=net.Listen("tcp",":1234")
	if e !=nil {
		log.Fatal("listen error",e)
	}
	go http.Serve(l,nil)
	os.Stdin.Read(make([]byte,1))
}
```
客户端

```golang
package main

func main(){
	//调用rpc服务端提供的方法之前 先与rpc服务建立连接
	client, err := rpc.DialHTTP("tcp", "127.0.0.1:1234")
	if err !=nil {
		log.Fatal("dialhttp erro",err)
		return
	}
	//同步调用服务端提供的方法
	args := &Args{7,8}
	var reply int
	err = client.Call("Arith.Multiply",args,&reply)
	if err !=nil{
		log.Fatal("Arith:%d*%d=%d\n", args.A, args.B, reply)
	}
	fmt.Printf("Arith:%d*%d = %d\n", args.A,args.B,reply)

	//异步调用
	quo :=Quotient{}

	divcall :=client.Go("Arith.Divide",args,&quo,nil)
	//使用select模型监听通道有数据时只需，否则执行后续程序
	for{
		select {
		case <-divcall.Done:
			fmt.Printf("商是%d,余数是%d\n",quo.Quo,quo.Rem)
		default:
			fmt.Print("继续向下执行。。。")
			time.Sleep(time.Second * 1)
		}
	}


}
```

