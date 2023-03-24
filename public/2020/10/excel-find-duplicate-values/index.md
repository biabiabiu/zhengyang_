# Excel查找重复值




Excel中，如何用多种不同的方法找出表中的重复数据？

<!--more-->

#### 条件格式法

自Excel 2010开始就内设了标识重复项的功能

先选定一块区域，在`开始`→`条件格式`→`突出显示单元格规则`→`重复值`，就可以把重复数据及所在单元格标记出来

<center>
    <img class="jf-image-shadow" src="/images/gif/excel-find-duplicate-values1.gif" title="条件格式法" width="500px" />
</center>

{{< admonition >}}

该方法只可以定位重复的数据而无法筛选出来

{{< /admonition >}}

#### 高级筛选法

在`数据`→`筛选`→`高级`→ `高级筛选`

<center>
    <img class="jf-image-shadow" src="/images/gif/excel-find-duplicate-values2.gif" title="高级筛选法" width="500px" />
</center>

`方式` 根据自己需要选择

`列表区域` 即需要查找的内容

`复制到` 选择筛选结果存放位置

#### 函数法

##### COUNTIF函数

用于统计满足某个条件的单元格的数量，因此可以用来快速查找重复数据

<center>
    <img class="jf-image-shadow" src="/images/still-image/excel-find-duplicate-values-countif.jpg" title="COUNTIF函数" width="500px" />
</center>

{{< admonition >}}

计算条件，可以是数字，表达式或文本，如"London"，21，">55"等

{{< /admonition >}}

<center>
    <img class="jf-image-shadow" src="/images/gif/excel-find-duplicate-values3.gif" title="函数法" width="500px" />
</center>

图中使用的都是COUNTIF函数，两种不同的用法

标记重复值，COUNTIF会在绝对引用的单元格区域中，对所有数据出现的次数进行计数，所以AF6831903查找后的结果为3，即出现了三次，这种结果和前面的条件格式法结果类似，标记出哪些是重复项，并计算了重复多少次

标记第n次重复项，公式每次选定的区域都不相同，数据每出现一次都会计算当前区域出现的次数，如AF6831903后结果为1，2，3即表示第一次出现，第二次出现，第三次出现...

#### 数据透视法

用数据透视表也可以快速地查找出重复项

<center>
    <img class="jf-image-shadow" src="/images/gif/excel-find-duplicate-values4.gif" title="数据透视法" width="500px" />
</center>


以上



