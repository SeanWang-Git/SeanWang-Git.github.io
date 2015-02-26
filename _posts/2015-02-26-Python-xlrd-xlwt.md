---
layout: post 
title: Python-xlrd-xlwt-xlutils
---


Python中一般使用xlrd库来读取Excel文件，使用xlwt库来生成Excel文件，使用xlutils库复制和修改Excel文件。这三个库只支持到Excel2003。python-excel主页地址：http://www.python-excel.org/

xlrd
---
地址：https://pypi.python.org/pypi/xlrd

github地址：https://github.com/python-excel/xlrd

打开excel文件，获取一个Book()对象：
    
    import xlrd
    book = xlrd.open_workbook("myfile.xls")
获取sheets数目：
    
    >>> book.nsheets
    3
获取sheets列表：
    
    >>> book.sheets()
    [<xlrd.sheet.Sheet object at 0x01A93970>, <xlrd.sheet.Sheet object at 0x01A93950>, <xlrd.sheet.Sheet object at 0x01A93E70>]
获取sheets name列表：
    
    book.sheet_names()
    [u'Sheet1', u'Sheet2', u'Sheet3']
获取Book()中的Sheet：
    
    sheet = book.sheets()[0]          #sheets返回一个sheet列表
    sheet = book.sheet_by_index(0)    #通过索引顺序获取
    sheet = book.sheet_by_name(u'Sheet1')#通过名称获取
获取行数，列数，名字：

	>>> sheet.nrows
	1002
	>>> sheet.ncols
	11
	>>> sheet.name
	u'Sheet1'
获取某行，某行值列表，某列，某列值列表：

	sheet.row(i)
	sheet.row_values(i)
	sheet.col(i)
	sheet.col_values(i)
获取单元格的值：

	cell = sheet.cell(i,j)
	cell_value = sheet.cell_value(i,j)
	cell_value = sheet.cell(i,j).value

需要注意的是，用xlrd读取excel是不能对其进行操作的：xlrd.open_workbook()方法返回xlrd.Book类型，是只读的，不能对其进行操作。

xlwt
---

地址：http://pypi.python.org/pypi/xlwt，适用于python2.3-2.7

xlwt-future：https://pypi.python.org/pypi/xlwt-future/0.8.0，适用于Python 2.6-3.3

github地址：https://github.com/python-excel/xlwt
创建一个Excel文件并创建一个Sheet：

	from xlwt import *
	book = Workbook()
	sheet = book.add_sheet('Sheet1')
	book.save('myExcel.xls')

Workbook类可以有encoding和style\_compression参数。

encoding，设置字符编码，style\_compression，表示是否压缩。

这样设置：w = Workbook(encoding='utf-8')，就可以在excel中输出中文了。默认是ascii。
向sheet写入内容：

	sheet.write(r, c, label="", style=Style.default_style)

简单写入：

	sheet.write(0, 0, label = 'Row 0, Column 0 Value')

设置格式写入：

	font = xlwt.Font() # 字体
	font.name = 'Times New Roman'
	font.bold = True
	font.underline = True
	font.italic = True
	style = xlwt.XFStyle() # 创建一个格式
	style.font = font # 设置格式字体
	sheet.write(1, 0, label = 'Formatted value', style) # Apply the Style to the Cell
	book.save('myExcel.xls')

写入日期：

	style = xlwt.XFStyle()
	style.num_format_str = 'M/D/YY' # Other options: D-MMM-YY, D-MMM, MMM-YY, h:mm, h:mm:ss, h:mm, h:mm:ss, M/D/YY h:mm, mm:ss, [h]:mm:ss, mm:ss.0
	sheet.write(0, 0, datetime.datetime.now(), style)

写入公式：

	sheet.write(0, 0, 5) # Outputs 5
	sheet.write(0, 1, 2) # Outputs 2
	sheet.write(1, 0, xlwt.Formula('A1*B1')) # 输出 "10" (A1[5] * A2[2])
	sheet.write(1, 1, xlwt.Formula('SUM(A1,B1)')) # 输出 "7" (A1[5] + A2[2])

写入链接：

	sheet.write(0, 0, xlwt.Formula('HYPERLINK("http://www.google.com";"Google")')) #输出 "Google"链接到http://www.google.com

xlutils
---

地址：http://pythonhosted.org/xlutils/

github地址：https://github.com/python-excel/xlutils

xlutils.copy.copy(wb)

复制一个xlrd.Book对象，生成一个xlwt.Workbook对象，可以对xlwt.Workbook进行修改。

	from xlrd import open_workbook
	from xlutils.copy import copy
	book = open_workbook('myExcel.xls')
	wbook = copy(book)  #wbook即为xlwt.WorkBook对象
	wsheet = wbook.get_sheet(0)  #通过get_sheet()获取的sheet有write()方法
	wsheet.write(0, 0, 'value')
	wb.save('myExcel.xls')
