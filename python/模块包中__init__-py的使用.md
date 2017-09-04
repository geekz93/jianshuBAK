- 在 `__init__.py `中导入模块中的文件:
目录结构:
```
gcode
    |--lbc
    |   |--__init__.py
    |   |--lbc.py
    |--test.py
```
在 `test.py` 中使用模块包中的 `lbc.py`模块: 通过`lbc.lbc`使用
```
__init.py__:
from lbc import lbc
test.py:
import lbc
```
说明: 在 `test.py` 中 import 的 lbc 时 lbc 模块包, 在导入模块包的时候系统会先执行`__init__.py`文件, 因此将 `lbc.py` 模块从 lbc 模块包中导入了

- 导入模块包中的全部模块: 
`__init__.py `中还有一个重要的变量，叫做` __all__`。我们有时会使出一招“全部导入”，也就是这样：
`from PackageName import *`
这时 import 就会把注册在包 `__init__.py` 文件中` __all__ `列表中的子模块和子包导入到当前作用域中来。比如：
文件
```
__init__.py:
__all__ = ["Module1", "Module2", "subPackage1", "subPackage2"]```
