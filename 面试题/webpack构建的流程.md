# webpack构建的流程

webpack启动后，从entry开始，递归解析entry依赖的所有module，找到每个module.rules里配置的loader进行相应的转换处理，对module转换后，解析出这些module所依赖的其他模块，解析的结果是一个一个的chunk，最后webpack会将所以chunk转换成文件输出的output。在整个构建流程中，webpack会在恰当的时机执行plugin里定义的插件，从而完成plugin插件的任务。

entry：模块入口，使得源文件加入到构建流程中

output：配置如何输出代码的

module：配置各种类型的模块的处理规则

plugin：配置扩展插件的

derServer: 实现本地服务：包括http服务 模块热替换  source map等服务

