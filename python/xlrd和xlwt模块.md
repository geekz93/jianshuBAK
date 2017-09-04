例子: http://www.jb51.net/article/60510.htm

- 设置宽度 :http://www.knowsky.com/886361.html
- 设置单元格背景: http://www.crifan.com/python_xlwt_set_cell_background_color/

## 插入图片
下面例子使用 insert_bitmap 来插入图片。
```
from xlwt import *
w = Workbook()
ws = w.add_sheet('Image')
ws.insert_bitmap('python.bmp', 2, 2)
ws.insert_bitmap('python.bmp', 10, 2)
w.save('image.xls')
```
