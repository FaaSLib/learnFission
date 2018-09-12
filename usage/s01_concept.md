# 01 Concept

简单来说 FaaS(Function as a service) 就是客户提供一个函数，服务方保证在需要时快速调用该函数。下面将介绍 fission 的基础概念，方便后续分析。

## 基本概念

基本的概念有 function, package, env, trigger。

function 即一个函数。他可以是一个代码文件中的一个函数。或者一个 package 中的一个函数。

package 即一个包。通常是一组代码文件经过一个构建步骤得到。

env 即某种语言及运行框架构成的运行环境。通常 function 在使用时需要与 env 进行"连接"。这里的"连接"视具体语言具体运行框架不同而不同。

trigger 即触发器。有 http, timer, message queue, kubernetes event 等不同类型。最简单的用法就是 http 请求触发 http trigger ，进而发起指定 function 的调用。

