# Module模块化

CommonJS导出:

module.exports

Commont导入:

require()

如果想要导入某个属性可以用解构赋值比如：const {username} = require(‘./Module’)

ES Module导出：

export {obj，username}

还有export default命令  这个是模块指定默认输出。这是为了方便导入模块时候为该函数或变量取任意名字

导入：

import { obj, username} from './Module.js'

