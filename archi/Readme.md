# Architecture

- namespaces

## namespaces

- fission
- fission-builder
- fission-function

`fission` namespace 运行所有自身组件。

`fission-builder` 运行构件组建。package 和 function 的构建步骤在这里进行。

`fission-function` 运行 env，即 function 的运行环境。

## ns `fission-function`

该 ns 存放运行环境。通常会看到 poolmgr 类型的容器池。每个 pod 有两个容器。运行 function 的容器镜像是 function 所指定的 env 中设置好的。另一个容器负责拉取 function。

## ns `fission`

该 ns 中有 6 个 service, 10 个 deployment, 1 个 daemonset。如下

```
service/controller      
service/executor        
service/influxdb        
service/nats-streaming  
service/router          
service/storagesvc      

daemonset.apps/logger   

deployment.apps/buildermgr       
deployment.apps/controller       
deployment.apps/executor         
deployment.apps/influxdb         
deployment.apps/kubewatcher      
deployment.apps/mqtrigger        
deployment.apps/nats-streaming   
deployment.apps/router           
deployment.apps/storagesvc       
deployment.apps/timer            
```

简单进行分类。

- trigger
    - router
    - timer
    - mqtrigger
    - kubewatcher
- buildermgr
- controller
- executor
- influxdb
- storagesvc
- logger