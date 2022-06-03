<p data-nodeid="910">在上一节课中，我们学习了如何使用 pandas 的函数来从多种数据源：csv、excel 和 html 网页。其中不管是哪一种数据读取的方式，最终返回的都是一个 DataFrame 对象。</p>
<p data-nodeid="911">对于 DataFrame 对象，上一讲我们只是简单将其打印出来，这一讲我们来学习围绕 DataFrame 的基本操作（添加行、列，删除行、列，排序等），除了 DataFrame，本讲我们也会学习另外一个重要的 pandas 数据结构: Series。</p>
<p data-nodeid="912">我们首先介绍 pandas 中的三个最常见的概念：index、Series 和 DataFrame。</p>
<h3 data-nodeid="913">数据的“目录”： index</h3>
<p data-nodeid="914">index 也叫索引，索引是计算机科学中非常常见的概念，你可能听起来会有点陌生，但其实应该很早之前就打过交道了。比如看一本书，书的目录就是书本内容的索引。所以通俗意义上，索引可以理解为就是存储了如何访问某块数据方式的数据。拿目录的例子来说，目录本身也是数据，但这个数据的内容是如何访问另一块数据（书的正文）。</p>
<p data-nodeid="915">在我们之前的学习中，我们也或多或少和索引打过交道。比如我们通过列表的下标访问列表的某个元素，比如 a[5] ，这个 5 也叫列表的索引。字典的场景中，我们通过 key 来访问字典中的某个元素，比如: student["name"]，这个 "name" 的字符串，也属于字典的索引。</p>
<h3 data-nodeid="916">一维数据序列：Series</h3>
<p data-nodeid="917">Series 本身是一种数据类型，很像我们之前打过交道的列表，是存储多个数据元素的容器。事实上，我们也可以直接使用一个列表来创建一个 Series。但与列表不同的是，Series 一般由两部分组成：index 和 values。</p>
<ul data-nodeid="918">
<li data-nodeid="919">
<p data-nodeid="920">values 容易理解，顾名思义就是存储了 Series 里面的所有元素的值，所以 values 部分可以认为就是和列表是等价的。</p>
</li>
<li data-nodeid="921">
<p data-nodeid="922">index 部分代表代表 Series 的<strong data-nodeid="1137">索引</strong>。根据上面对于索引的定义，index 部分的数据就是为了能方便地定位到 values 里面的数据。</p>
</li>
</ul>
<p data-nodeid="923">Series 有一个单独的索引项，这就使得它既支持类似列表一样的数字索引，也支持类似字典一样的用字符串或者其他 Python 对象来做索引。对于 Series，可以简单理解成是一个列表和字典的集合体。</p>
<p data-nodeid="924">接下来我们用几个实例来简单介绍一下 Series 的概念。</p>
<h4 data-nodeid="925">（1）直接从列表创建 Series</h4>
<p data-nodeid="926">新建 chapter12 文件夹，打开 VS code 打开该文件夹，然后新建新的 notebook，命名为 chapter12.ipynb ，并保存到上述文件夹。</p>
<pre class="lang-python" data-nodeid="927"><code data-language="python"><span class="hljs-keyword">import</span>&nbsp;pandas&nbsp;<span class="hljs-keyword">as</span>&nbsp;pd
<span class="hljs-comment">#&nbsp;通过列表创建&nbsp;Series</span>
ser1&nbsp;=&nbsp;pd.Series([<span class="hljs-number">1</span>,<span class="hljs-number">3</span>,<span class="hljs-number">5</span>,<span class="hljs-number">7</span>])
<span class="hljs-comment">#&nbsp;通过&nbsp;notebook&nbsp;打印&nbsp;ser1</span>
ser1
</code></pre>
<p data-nodeid="928">输出显示如下：</p>
<pre class="lang-java" data-nodeid="929"><code data-language="java"><span class="hljs-number">0</span>    <span class="hljs-number">1</span>
<span class="hljs-number">1</span>    <span class="hljs-number">3</span>
<span class="hljs-number">2</span>    <span class="hljs-number">5</span>
<span class="hljs-number">3</span>    <span class="hljs-number">7</span>
dtype: int64
</code></pre>
<p data-nodeid="930">输出有两列，第一列是 index，第二列是 values， values 就是我们传入的列表，而 index 则是对应的序号。当我们只使用列表来创建 Series 对象时，会生成默认的索引。即类似列表那样，每一个元素的位置作为索引。Series 对象也具备 index 和 values 属性，这样我们可以单独访问这两个部分。</p>
<pre class="lang-python" data-nodeid="931"><code data-language="python">print(<span class="hljs-string">"values:&nbsp;"</span>,&nbsp;ser1.values)
print(<span class="hljs-string">"index:&nbsp;"</span>,&nbsp;ser1.index)
</code></pre>
<p data-nodeid="932">从以下输出结果可以看到，values 其实就是我们传入的列表，而 index 则是一个 RangeIndex 的对象。</p>
<pre class="lang-java" data-nodeid="933"><code data-language="java">values:  [<span class="hljs-number">1</span> <span class="hljs-number">3</span> <span class="hljs-number">5</span> <span class="hljs-number">7</span>]
index:  RangeIndex(start=<span class="hljs-number">0</span>, stop=<span class="hljs-number">4</span>, step=<span class="hljs-number">1</span>)
</code></pre>
<p data-nodeid="934">对于这个 Series 对象，我们可以通过 index 的值来获得对应 values 里面的值。比如 index 等于1 对应的是 values 里面的 3。在代码中想要获得 1 对应的值就可以这样：</p>
<pre class="lang-python" data-nodeid="935"><code data-language="python">ser1[<span class="hljs-number">1</span>]
</code></pre>
<p data-nodeid="936">输出</p>
<pre class="lang-java" data-nodeid="937"><code data-language="java"><span class="hljs-number">3</span>
</code></pre>
<h4 data-nodeid="938">（2）创建 Series，并指定索引</h4>
<p data-nodeid="939">在上面的例子中，我们直接从一个列表创建了 Series，Series 为其分配了默认的 index，即元素在列表中的位置作为其对应的 index，比如 5 是列表 1,3,5,7 中的第三个数字，则它的 index 就是 2（从 0 开始数起）。</p>
<p data-nodeid="940">除了这种方式，Series 还支持我们在创建的时候指定对应的索引。</p>
<pre class="lang-python" data-nodeid="941"><code data-language="python"><span class="hljs-comment">#&nbsp;使用列表创建&nbsp;Series，并指定其索引为另一个列表</span>
ser2&nbsp;=&nbsp;pd.Series([<span class="hljs-number">1</span>,<span class="hljs-number">3</span>,<span class="hljs-number">5</span>,<span class="hljs-number">7</span>],&nbsp;index=[<span class="hljs-string">"a"</span>,&nbsp;<span class="hljs-string">"b"</span>,&nbsp;<span class="hljs-string">"c"</span>,&nbsp;<span class="hljs-string">"d"</span>])
<span class="hljs-comment">#&nbsp;使用&nbsp;notebook&nbsp;打印&nbsp;ser2</span>
ser2
</code></pre>
<p data-nodeid="942">输出为：</p>
<pre class="lang-java" data-nodeid="943"><code data-language="java">a    <span class="hljs-number">1</span>
b    <span class="hljs-number">3</span>
c    <span class="hljs-number">5</span>
d    <span class="hljs-number">7</span>
dtype: int64
</code></pre>
<p data-nodeid="944">可以看到，我们指定了一个由 4 个字符串的列表作为数字列表的索引。两个列表的元素是一一对应的关系，比如字符串 "a" 就是数字 1 的索引，字符串 "b" 就是数字 3 的索引。我们可以验证一下。</p>
<pre class="lang-python" data-nodeid="945"><code data-language="python">print(ser2[<span class="hljs-string">"d"</span>])
</code></pre>
<p data-nodeid="946">输出如下，可以看到我们通过索引 "d" ，确实拿到了数字 7。</p>
<pre class="lang-java" data-nodeid="947"><code data-language="java"><span class="hljs-number">7</span>
</code></pre>
<p data-nodeid="948">现在我们来看一下 ser2 的 values 和 index 的值</p>
<pre class="lang-python" data-nodeid="949"><code data-language="python">print(<span class="hljs-string">"values:"</span>,&nbsp;ser2.values)
print(<span class="hljs-string">"index:"</span>,&nbsp;ser2.index)
</code></pre>
<p data-nodeid="950">输出</p>
<pre class="lang-java" data-nodeid="951"><code data-language="java">values: [<span class="hljs-number">1</span> <span class="hljs-number">3</span> <span class="hljs-number">5</span> <span class="hljs-number">7</span>]
index: Index([<span class="hljs-string">'a'</span>, <span class="hljs-string">'b'</span>, <span class="hljs-string">'c'</span>, <span class="hljs-string">'d'</span>], dtype=<span class="hljs-string">'object'</span>)
</code></pre>
<p data-nodeid="3225">values 和第一个例子一样，但 values 这次就不是 RangeIndex 对象了，而是一个 Index 对象，里面保存了我们传入的作为索引的字符串数组。</p>
<p data-nodeid="3226">总结一下， Series 可以看成是高级的列表或者字典，当不指定 index 的时候，Series 会生成默认的位置索引，这样的 Series 就像是一个列表。而当我们指定了 index 之后，则可以通过 index 列表中的元素来访问对应的 values 中的元素，就像字典的 key-value 结构一样。</p>

<p data-nodeid="953">整体来说，<strong data-nodeid="1174">Series 通过将 index 和 values 分别存储的机制，实现了列表和字典的结合。</strong></p>
<h3 data-nodeid="954">二维数据表：DataFrame</h3>
<p data-nodeid="955">学习完了 Series，现在我们来看上一讲经常出现的 DataFrame。在上一讲的学习中，我们都是从各种文件中加载数据，之后直接存储为 DataFrame。这个部分我们来一步步地揭开 DataFrame 的神秘面纱。</p>
<h4 data-nodeid="956">（1）DataFrame 的组成</h4>
<p data-nodeid="957">根据上一讲我们学习的内容，DataFrame 是一个由行和列组成的二维表格。相信你已经猜到了，DataFrame 其实就是由 Series 组成的，DataFrame 的某一行，或者某一列都是一个 Series。</p>
<p data-nodeid="958">口说无凭，我们通过代码来确认一下。将上一讲中的 tv_rating.csv 文件拷贝到 chapter12 目录。并新建 Cell， 输入如下代码：</p>
<pre class="lang-python" data-nodeid="959"><code data-language="python"><span class="hljs-comment">#&nbsp;加载电视剧评分数据</span>
df_rating&nbsp;=&nbsp;pd.read_csv(<span class="hljs-string">"tv_rating.csv"</span>)
<span class="hljs-comment">#&nbsp;输出评分的&nbsp;DataFrame</span>
df_rating
</code></pre>
<p data-nodeid="4151" class="">输出为：<br>
<img src="https://s0.lgstatic.com/i/image6/M00/3F/3E/CioPOWCc5n2AWoiKAAIKRi7SPjI316.png" alt="Drawing 0.png" data-nodeid="4156"></p>

<p data-nodeid="961">在上述表格中，无论是列（比如标题、评分）或者行（比如第二行、第三行）都是 Series。其中 title、rating、stars 则是列的索引。而 0、1、2...3599 是行的索引。</p>
<p data-nodeid="962">我们可以通过列名作为索引，来单独输出某一列，比如评分这一列。</p>
<pre class="lang-python" data-nodeid="963"><code data-language="python"><span class="hljs-comment">#&nbsp;获取&nbsp;rating&nbsp;这一列，存储在ser_rating&nbsp;变量中</span>
ser_rating&nbsp;=&nbsp;df_rating[<span class="hljs-string">"rating"</span>]
<span class="hljs-comment">#&nbsp;输出&nbsp;ser_rating&nbsp;这个&nbsp;Series</span>
print(ser_rating)
<span class="hljs-comment">#&nbsp;分割一下，方便查看</span>
print(<span class="hljs-string">"------------分割一下------------"</span>)
<span class="hljs-comment">#&nbsp;查看数据的类型</span>
print(type(ser_rating))
</code></pre>
<p data-nodeid="964">输出结果为：</p>
<pre class="lang-java" data-nodeid="965"><code data-language="java"><span class="hljs-number">0</span>       <span class="hljs-number">3.7</span>分
<span class="hljs-number">1</span>       <span class="hljs-number">4.0</span>分
<span class="hljs-number">2</span>       <span class="hljs-number">4.6</span>分
<span class="hljs-number">3</span>       <span class="hljs-number">3.4</span>分
<span class="hljs-number">4</span>       <span class="hljs-number">4.4</span>分
        ... 
<span class="hljs-number">3595</span>    <span class="hljs-number">4.0</span>分
<span class="hljs-number">3596</span>    <span class="hljs-number">4.0</span>分
<span class="hljs-number">3597</span>    <span class="hljs-number">1.0</span>分
<span class="hljs-number">3598</span>    <span class="hljs-number">2.0</span>分
<span class="hljs-number">3599</span>    <span class="hljs-number">4.6</span>分
Name: rating, Length: <span class="hljs-number">3600</span>, dtype: object
------------分割一下------------
&lt;<span class="hljs-class"><span class="hljs-keyword">class</span> '<span class="hljs-title">pandas</span>.<span class="hljs-title">core</span>.<span class="hljs-title">series</span>.<span class="hljs-title">Series</span>'&gt;
</span></code></pre>
<p data-nodeid="5079">可以看到，分数的这一列被打印出来，格式和上面学习的 Series 是一样的，左边是 index，右边是 values。之后我们通过 type 函数获得了 ser_rating 变量的类型，确实也是 Series。</p>
<p data-nodeid="5080">除了输出某一列，我们还可以用行索引，来单独输出某一行。比如我们输出第二行：刘老根第三部，对应的索引是 1。我们可以用如下的代码获取这一行。</p>

<pre class="lang-python" data-nodeid="967"><code data-language="python"><span class="hljs-comment">#&nbsp;DataFrame&nbsp;通过&nbsp;loc&nbsp;函数可以查看行索引对应的值</span>
<span class="hljs-comment">#&nbsp;取出行索引为&nbsp;1&nbsp;的行，存储在&nbsp;ser_1&nbsp;变量中</span>
ser_1&nbsp;=&nbsp;df_rating.loc[<span class="hljs-number">1</span>]
<span class="hljs-comment">#&nbsp;打印&nbsp;ser1&nbsp;这个&nbsp;Series</span>
print(df_rating.loc[<span class="hljs-number">1</span>])
<span class="hljs-comment">#&nbsp;分割一下，方便查看</span>
print(<span class="hljs-string">"------------分割一下------------"</span>)
<span class="hljs-comment">#&nbsp;查看数据的类型</span>
print(type(df_rating.loc[<span class="hljs-number">1</span>]))
</code></pre>
<p data-nodeid="968">输出为：</p>
<pre class="lang-java" data-nodeid="969"><code data-language="java">title                  刘老根第三部
rating                   <span class="hljs-number">4.0</span>分
stars     主演赵本山,范伟,李静,闫学晶,王小宝
Name: <span class="hljs-number">1</span>, dtype: object
------------分割一下------------
&lt;<span class="hljs-class"><span class="hljs-keyword">class</span> '<span class="hljs-title">pandas</span>.<span class="hljs-title">core</span>.<span class="hljs-title">series</span>.<span class="hljs-title">Series</span>'&gt;
</span></code></pre>
<p data-nodeid="6007">可以看到，我们拿到的 ser_1 仍然是一个 Series 类型的对象。左边的 title、rating、stars是index，右边的"刘老根第三部""4.0分" 等是 values。因为 ser_1 是一个 Series，所以如果我们要拿这一行中的某个数据，比如评分，直接写 ser_1["rating"] 就可以实现。</p>
<p data-nodeid="6008">对比通过行索引取出的行 Series 和 通过列索引取出的列 Series 不难发现，<strong data-nodeid="6034">列 Series 的 index 是 DataFrame 的行头，而行 Series 的 index 则是 DataFrame 的列名</strong>。</p>

<h4 data-nodeid="971">（2）DataFrame 的创建</h4>
<p data-nodeid="972">既然 DataFrame 是一个个 Series 组成的，那自然我们可以用 Series 来构造出 DataFrame。</p>
<p data-nodeid="973">构造 DataFrame 最常见的方式是用多个行 Series 的形式来创建，不同的行 Series 的长度应该是一致的（因为表格中每一行的元素个数都需要相等）。</p>
<p data-nodeid="974">我们以如下表格为例，将其直接创建为一个 DataFrame。</p>
<p data-nodeid="6957" class=""><img src="https://s0.lgstatic.com/i/image6/M00/3F/3E/CioPOWCc5pGAY4wvAABEPmw2qjE441.png" alt="Drawing 1.png" data-nodeid="6960"></p>


<p data-nodeid="1005">新建 Cell ，输入如下代码：</p>
<pre class="lang-python" data-nodeid="1006"><code data-language="python"><span class="hljs-comment">#&nbsp;将列索引保存在&nbsp;index_arr&nbsp;变量中</span>
index_arr&nbsp;=&nbsp;[<span class="hljs-string">"姓名"</span>,&nbsp;<span class="hljs-string">"年龄"</span>,&nbsp;<span class="hljs-string">"籍贯"</span>,&nbsp;<span class="hljs-string">"部门"</span>]
<span class="hljs-comment">#&nbsp;构建小明、小亮、小E的行&nbsp;Series，并使用我们创建好的&nbsp;index_arr&nbsp;作为&nbsp;Series&nbsp;的index</span>
ser_xiaoming&nbsp;=&nbsp;pd.Series([<span class="hljs-string">"小明"</span>,&nbsp;<span class="hljs-number">22</span>,&nbsp;<span class="hljs-string">"河北"</span>,<span class="hljs-string">"IT部"</span>],&nbsp;index=&nbsp;index_arr)
ser_xiaoliang&nbsp;=&nbsp;pd.Series([<span class="hljs-string">"小亮"</span>,&nbsp;<span class="hljs-number">25</span>,&nbsp;<span class="hljs-string">"广东"</span>,<span class="hljs-string">"IT部"</span>],&nbsp;index&nbsp;=&nbsp;index_arr)
ser_xiaoe&nbsp;=&nbsp;pd.Series([<span class="hljs-string">"小E"</span>,&nbsp;<span class="hljs-number">23</span>,&nbsp;<span class="hljs-string">"四川"</span>,<span class="hljs-string">"财务部"</span>],&nbsp;index=&nbsp;&nbsp;index_arr)
<span class="hljs-comment">#&nbsp;直接将三个&nbsp;Series&nbsp;以列表的形式作为&nbsp;DataFrame&nbsp;的参数，创建&nbsp;DataFrame</span>
df_info&nbsp;=&nbsp;pd.DataFrame([ser_xiaoming,&nbsp;ser_xiaoliang,&nbsp;ser_xiaoe])
<span class="hljs-comment">#&nbsp;使用&nbsp;notebook&nbsp;打印&nbsp;DataFrame</span>
df_info
</code></pre>
<p data-nodeid="7793" class="">输出<br>
<img src="https://s0.lgstatic.com/i/image6/M00/3F/3E/CioPOWCc5piAZtVwAAAxdFwHom8557.png" alt="Drawing 2.png" data-nodeid="7798"></p>

<p data-nodeid="1008">可以看到，表格已经被成功的打印出来，这说明我们已经将内容正确构建出了 DataFrame。</p>
<h3 data-nodeid="1009">基本操作</h3>
<p data-nodeid="1010">接下来这一节，我们来讲解一下 DataFrame 和 Series 的常见操作。</p>
<h4 data-nodeid="1011">（1）添加行</h4>
<p data-nodeid="1012">DataFrame 提供了 append 的方法，用于添加一行，用法如下：</p>
<pre class="lang-python" data-nodeid="1013"><code data-language="python"><span class="hljs-comment">#&nbsp;新建一个行&nbsp;Series，存储在&nbsp;ser_xiaoh变量中</span>
ser_xiaoh&nbsp;=&nbsp;pd.Series([<span class="hljs-string">"小红"</span>,&nbsp;<span class="hljs-number">28</span>,&nbsp;<span class="hljs-string">"福建"</span>,&nbsp;<span class="hljs-string">"财务部"</span>],&nbsp;index&nbsp;=&nbsp;index_arr)
<span class="hljs-comment">#&nbsp;调用&nbsp;append&nbsp;方法添加到DataFrame&nbsp;中</span>
<span class="hljs-comment">#&nbsp;设置&nbsp;ignore_index&nbsp;的含义是让&nbsp;DataFrame&nbsp;自动生成行索引</span>
<span class="hljs-comment">#&nbsp;调用&nbsp;append&nbsp;之后，会返回一个新的&nbsp;DataFrame，我们将其保存回&nbsp;df_info&nbsp;变量</span>
df_info&nbsp;=&nbsp;df_info.append(ser_xiaoh,&nbsp;ignore_index=&nbsp;<span class="hljs-literal">True</span>)
<span class="hljs-comment">#&nbsp;查看添加后的DataFrame</span>
df_info
</code></pre>
<p data-nodeid="8631" class="">输出后可以看到，小红的记录已经追加到了末尾。<br>
<img src="https://s0.lgstatic.com/i/image6/M01/3F/36/Cgp9HWCc5qCACtioAABAKcY_wDE691.png" alt="Drawing 3.png" data-nodeid="8636"></p>

<h4 data-nodeid="1015">（2）添加列</h4>
<p data-nodeid="1016">添加一列一般有两种情况，如果我们要添加的列，所有行的值都相同的话，我们可以直接以单个值赋值给新添加的列 Series 即可。如下所示：</p>
<pre class="lang-python" data-nodeid="1017"><code data-language="python"><span class="hljs-comment">#&nbsp;直接将新添加的列名当作&nbsp;DataFrame&nbsp;的列索引，对其赋新的值</span>
df_info[<span class="hljs-string">"考核结果"</span>]&nbsp;=&nbsp;<span class="hljs-string">"合格"</span>
<span class="hljs-comment">#&nbsp;查看</span>
df_info
</code></pre>
<p data-nodeid="9469" class="">输出为：<br>
<img src="https://s0.lgstatic.com/i/image6/M00/3F/3E/CioPOWCc5qmAW_O_AABSkQKX3zY822.png" alt="Drawing 4.png" data-nodeid="9474"></p>

<p data-nodeid="1019">但如果新添加的列，每一行的内容不是完全一样时，就需要我们将一个新的 Series 赋值给 DataFrame 针对新列名的列 Series。</p>
<pre class="lang-python" data-nodeid="1020"><code data-language="python"><span class="hljs-comment">#&nbsp;将新添加的&nbsp;Series&nbsp;赋值给&nbsp;DataFrame&nbsp;中新列名对应的列&nbsp;Series</span>
df_info[<span class="hljs-string">"考核结果"</span>]&nbsp;=&nbsp;pd.Series([<span class="hljs-string">"合格"</span>,&nbsp;<span class="hljs-string">"良好"</span>,&nbsp;<span class="hljs-string">"优秀"</span>,&nbsp;<span class="hljs-string">"良好"</span>])
<span class="hljs-comment">#&nbsp;查看</span>
df_info
</code></pre>
<p data-nodeid="1021">输出结果为：</p>
<p data-nodeid="10307" class=""><img src="https://s0.lgstatic.com/i/image6/M01/3F/36/Cgp9HWCc5rCAYrOFAABTPK_CVu0026.png" alt="Drawing 5.png" data-nodeid="10310"></p>

<p data-nodeid="1023">可以看到，我们的列已经对应到了不同的行上面。有一点值得注意的是，我们第一次已经添加了“考核结果”这一列，每一行的值都是合格。后来我们对这一列赋值了一个新的 Series，修改了它的值。</p>
<p data-nodeid="1024">所以，<strong data-nodeid="1279">当我们对 DataFrame 某个列名对应的列 Series 赋值，当列名不存在的时候，则会新建对应的列，而当列名存在时，则会修改原先列的值。</strong></p>
<p data-nodeid="1025">所以这个技术既能创建新的一列，也可以修改已有的列。</p>
<h4 data-nodeid="1026">（3）删除行或列</h4>
<p data-nodeid="1027">DataFrame 提供了 drop 方法来删除某一行或者某一列。</p>
<p data-nodeid="1028">我们先以删除列举例，比如要删除刚才我们添加的“考核结果”这一列</p>
<pre class="lang-python" data-nodeid="1029"><code data-language="python"><span class="hljs-comment">#&nbsp;labels&nbsp;是要删除的列名</span>
<span class="hljs-comment"># axis&nbsp;=&nbsp;1&nbsp;代表要删除的是列</span>
<span class="hljs-comment">#&nbsp;inplace&nbsp;=&nbsp;True&nbsp;代表删除直接在&nbsp;df_info&nbsp;中生效。</span>
df_info.drop(labels&nbsp;=&nbsp;<span class="hljs-string">"考核结果"</span>,&nbsp;axis=<span class="hljs-number">1</span>,&nbsp;inplace=&nbsp;<span class="hljs-literal">True</span>)
<span class="hljs-comment">#&nbsp;查看</span>
df_info
</code></pre>
<p data-nodeid="1030">输出结果如下，可以看到考核结果一列已经被删除。</p>
<p data-nodeid="11143" class=""><img src="https://s0.lgstatic.com/i/image6/M00/3F/3F/CioPOWCc5ryAc7NwAAA-94Kbhuk971.png" alt="Drawing 6.png" data-nodeid="11146"></p>

<p data-nodeid="1032">接下来是删除行，以删除小 E 这一行为例：</p>
<pre class="lang-python" data-nodeid="1033"><code data-language="python"><span class="hljs-comment">#&nbsp;labels&nbsp;是要删除行的&nbsp;index，小E的index是2</span>
<span class="hljs-comment">#&nbsp;axis&nbsp;=&nbsp;0&nbsp;代表要删除的是行</span>
df_info.drop(labels=<span class="hljs-number">2</span>,&nbsp;axis=<span class="hljs-number">0</span>,&nbsp;inplace=<span class="hljs-literal">True</span>)
<span class="hljs-comment">#&nbsp;查看</span>
df_info
</code></pre>
<p data-nodeid="11979" class="">输出结果如下，可以看到，小 E 那一行记录已经被成功删除。<br>
<img src="https://s0.lgstatic.com/i/image6/M00/3F/3F/CioPOWCc5sKAbGHzAAAz6desnM8702.png" alt="Drawing 7.png" data-nodeid="11984"></p>

<h4 data-nodeid="1035">（4）单个单元格的查看与修改</h4>
<p data-nodeid="1036">在上面的操作中，整体还是以 Series 维度的操作为主。比如修改 Series，增加 Series。如果我们只需要查看和修改其中某一个单元格的内容，虽然也可以通过上面的方法，比如首先获得单元格所在的行 Series 或者列 Series，然后再用进一步的索引去获得单元格的内容。这样的方式一个比较麻烦，二是修改的时候可能会有问题。</p>
<p data-nodeid="1037">对于单个单元格的查看和修改，推荐的方式是使用 DataFrame 的 loc 属性，可以一步到位指定定位到单元格，假设我们需要查看小亮的籍贯，以及修改为广西这个任务为例，演示 loc 函数的用法。</p>
<p data-nodeid="1038">查看单元格：</p>
<pre class="lang-python" data-nodeid="1039"><code data-language="python"><span class="hljs-comment">#&nbsp;loc&nbsp;属性后面跟中括号，中括号里面第一个元素是行索引，第二个元素是列索引</span>
<span class="hljs-comment">#&nbsp;小亮的行索引是1，我们想查看籍贯，所以列索引就是籍贯</span>
df_info.loc[<span class="hljs-number">1</span>,&nbsp;<span class="hljs-string">"籍贯"</span>]
</code></pre>
<p data-nodeid="1040">输出为：</p>
<pre class="lang-java" data-nodeid="1041"><code data-language="java"><span class="hljs-string">'广东'</span>
</code></pre>
<p data-nodeid="1042">学会了查看之后，修改就比较简单了，直接给 loc 属性选出来的单元格赋值即可。</p>
<pre class="lang-python" data-nodeid="1043"><code data-language="python"><span class="hljs-comment">#&nbsp;对行索引为1，列索引为&nbsp;籍贯&nbsp;的单元格赋值，赋值&nbsp;广西</span>
df_info.loc[<span class="hljs-number">1</span>,&nbsp;<span class="hljs-string">"籍贯"</span>]&nbsp;=&nbsp;<span class="hljs-string">"广西"</span>
<span class="hljs-comment">#&nbsp;查看&nbsp;DataFrame</span>
df_info
</code></pre>
<p data-nodeid="1044">输出，可以看到，小亮的籍贯已经被修改为广西。</p>
<p data-nodeid="12817" class=""><img src="https://s0.lgstatic.com/i/image6/M01/3F/36/Cgp9HWCc5tCAS1kaAAA0AAgXGrA097.png" alt="Drawing 8.png" data-nodeid="12820"></p>

<h4 data-nodeid="1046">（5）DataFrame 的排序</h4>
<p data-nodeid="1047">在数据分析的任务中，对数据集进行排序是非常常见的诉求。拿我们电视剧评分的数据集来说，可能我们希望分析高分的电影和低分的电影分别都有些什么特征。做这样的分析，首先第一步就是需要将我们的 DataFrame 按评分排序。我们以之前我们从 csv 加载的 DataFrame, df_rating 为例。</p>
<p data-nodeid="1048">DataFrame 提供了 sort_values 方法来实现排序，用法如下。</p>
<pre class="lang-python" data-nodeid="1049"><code data-language="python"><span class="hljs-comment">#&nbsp;by&nbsp;参数代表要按&nbsp;rating&nbsp;这个列索引来排序</span>
<span class="hljs-comment">#&nbsp;inplace&nbsp;=&nbsp;True&nbsp;的含义和上面说的一样，代表更新当前的DataFrame，而不是返回一个新的</span>
df_rating.sort_values(by&nbsp;=&nbsp;<span class="hljs-string">"rating"</span>,&nbsp;inplace=<span class="hljs-literal">True</span>)
<span class="hljs-comment">#&nbsp;查看排序后的&nbsp;DataFrame</span>
df_rating
</code></pre>
<p data-nodeid="13653" class="">输出为：<br>
<img src="https://s0.lgstatic.com/i/image6/M01/3F/36/Cgp9HWCc5tiAQfY6AAGfifkZwD0970.png" alt="Drawing 9.png" data-nodeid="13658"></p>

<p data-nodeid="1051">可以看到，整个 DataFrame 不再是按行头的索引排序，而是按照电视剧的评分从低到高来排序了。</p>
<p data-nodeid="1052">如果想看从高到低呢？自然也是支持的。只需要将是否升序排序的参数：ascending 设置为False 即可。</p>
<pre class="lang-python" data-nodeid="1053"><code data-language="python"><span class="hljs-comment">#&nbsp;在刚才的基础上，增加&nbsp;ascending=False，代表按降序排序</span>
df_rating.sort_values(by=<span class="hljs-string">"rating"</span>,&nbsp;inplace=<span class="hljs-literal">True</span>,&nbsp;ascending=<span class="hljs-literal">False</span>)
<span class="hljs-comment">#&nbsp;查看</span>
df_rating
</code></pre>
<p data-nodeid="1054">输出如下所示，可以看到 DataFrame 已经变为评分从高到低排序了</p>
<p data-nodeid="14491" class=""><img src="https://s0.lgstatic.com/i/image6/M01/3F/36/Cgp9HWCc5uCASSpnAAGtWbCFw6U028.png" alt="Drawing 10.png" data-nodeid="14494"></p>

<h4 data-nodeid="1056">（6）取前 N 个和后 N 个</h4>
<p data-nodeid="1057">在排序后，我们对数据表要进行分析，比如对高分进行分析，我们往往需要看多几个条目。但是每次输出 DataFrame 的时候，Notebook 一般只会选择前五个和末尾五个组成摘要进行表格的输出。如果默认的表格打印不满足我们的需求，我们可以使用 DataFrame 的 head 函数和 tail 函数来输出前 N 个和 后 N 个的数据。</p>
<p data-nodeid="1058">举个例子，我们希望分别分析 20 条高分电视剧和 20 条低分电视剧。可以按如下方式实现：</p>
<pre class="lang-python" data-nodeid="1059"><code data-language="python"><span class="hljs-comment">#&nbsp;head&nbsp;函数返回&nbsp;DataFrame&nbsp;的前&nbsp;N&nbsp;条记录，N就是函数参数指定的值</span>
<span class="hljs-comment">#&nbsp;这里我们指定&nbsp;20&nbsp;</span>
df_rating.head(<span class="hljs-number">20</span>)
</code></pre>
<p data-nodeid="15327" class="">输出结果为：<br>
<img src="https://s0.lgstatic.com/i/image6/M00/3F/3F/CioPOWCc5uuAen7UAALh4MirY1g688.png" alt="Drawing 11.png" data-nodeid="15332"></p>

<p data-nodeid="1061">输出最后的 20 条的原理是类似的，只不过换成 tail 函数。</p>
<pre class="lang-python" data-nodeid="1062"><code data-language="python"><span class="hljs-comment">#&nbsp;tail&nbsp;函数，返回DataFrame&nbsp;的末尾的&nbsp;N&nbsp;条记录，N就是函数的参数</span>
<span class="hljs-comment">#&nbsp;这里的N，我们指定&nbsp;20</span>
df_rating.tail(<span class="hljs-number">20</span>)
</code></pre>
<p data-nodeid="1063">输出如下所示，可以看到这次输出了 20 条都是 1 分的数据。</p>
<p data-nodeid="16165" class=""><img src="https://s0.lgstatic.com/i/image6/M00/3F/3F/CioPOWCc5vOATptWAAM9wUAvcs8399.png" alt="Drawing 12.png" data-nodeid="16168"></p>

<h4 data-nodeid="1065">（7）获取 DataFrame 的行数和列数</h4>
<p data-nodeid="1066">很多时候，从数据文件加载为 DataFrame 的时候，我们首先会看这个 DataFrame 有多少行、多少列。 DataFrame 提供了 shape 属性来返回行数和列数的信息。</p>
<p data-nodeid="1067">shape 属性返回一个元组，这个数据结构我们之前没有学习过，不过你可以简单把他当一个列表用即可，shape 属性返回的元组有两个元素，第一个就是行数，第二个就是列数。</p>
<p data-nodeid="1068">比如那 df_rating 这个 DataFrame 为例，打印其行列数信息，代码如下：</p>
<pre class="lang-python" data-nodeid="1069"><code data-language="python"><span class="hljs-comment">#&nbsp;shape&nbsp;属性，返回一个元祖，第一个是行数，第二个元素是列数</span>
shape&nbsp;=&nbsp;df_rating.shape
<span class="hljs-comment">#&nbsp;打印行数和列数</span>
print(<span class="hljs-string">"行数:"</span>,&nbsp;shape[<span class="hljs-number">0</span>])
print(<span class="hljs-string">"列数:"</span>,&nbsp;shape[<span class="hljs-number">1</span>])
</code></pre>
<p data-nodeid="1070">输出后和我们数据集的情况是匹配的。</p>
<pre class="lang-java" data-nodeid="1071"><code data-language="java">行数: <span class="hljs-number">3600</span>
列数: <span class="hljs-number">3</span>
</code></pre>
<h3 data-nodeid="1072">小结</h3>
<p data-nodeid="1073">简单的总结一下今天学习到的内容。</p>
<p data-nodeid="1074">首先，我们学习了一个计算机领域非常重要的概念——索引。这也是 pandas 中 DataFrame 很多操作的基础。索引之于数据就像目录之于书本内容，我们通过索引从一堆数据的拿出我们想要的一个或者多个数据。</p>
<p data-nodeid="1075">然后，我们学习了 pandas 中的一维数据序列对象：Series。Series 融合了列表和字典的功能。通过把 index 和values 分开存储，让它既能按照列表使用，也能按照字典使用。</p>
<p data-nodeid="1076">之后，我们学习了 DataFrame 的基本概念，DataFrame 是由 Series 组成的二维数据表。DataFrame 的一行或者一列都是一个 Series。自然我们可以用多个行 Series 或者多个列 Series 来创建 DataFrame。</p>
<p data-nodeid="1077">最后，我们学习了 DataFrame 的基本操作。</p>
<ul data-nodeid="1078">
<li data-nodeid="1079">
<p data-nodeid="1080">添加行：用 append 方法</p>
</li>
<li data-nodeid="1081">
<p data-nodeid="1082">添加列：将新增加的列 Series 通过列名作为列索引赋值给 DataFrame 。</p>
</li>
<li data-nodeid="1083">
<p data-nodeid="1084">删除行或者列：用 drop 方法，通过 axis 参数控制删除行或删除列</p>
</li>
<li data-nodeid="1085">
<p data-nodeid="1086">单个单元格的查看与修改：loc 属性，中括号内第一个元素是行索引，第二个是列索引。</p>
</li>
<li data-nodeid="1087">
<p data-nodeid="1088">排序：用 sort_values 方法， by 参数指定要用哪一列作为排序标准，ascending 参数决定要升序还是降序。</p>
</li>
<li data-nodeid="1089">
<p data-nodeid="1090">取前 N 个和后 N 个：head 和 tail 函数，N 就是函数的参数。</p>
</li>
<li data-nodeid="1091">
<p data-nodeid="1092">获取行数和列数：shape 属性。</p>
</li>
</ul>
<p data-nodeid="1093">课后练习：</p>
<p data-nodeid="1094">为电视剧评分的 DataFrame，添加一列质量评级信息，列名为:"level"，规则是：</p>
<ul data-nodeid="1095">
<li data-nodeid="1096">
<p data-nodeid="1097">评分小于 2 分，则 level 为“低”；</p>
</li>
<li data-nodeid="1098">
<p data-nodeid="1099">大于等于2分，小于4分，则为“中”；</p>
</li>
<li data-nodeid="1100">
<p data-nodeid="1101">大于等于4分，则为“高”。</p>
</li>
</ul>
<p data-nodeid="1102">添加完后，打印出增加之后的 DataFrame。</p>
<hr data-nodeid="1103">
<p data-nodeid="1104">答案：</p>
<pre class="lang-python" data-nodeid="1105"><code data-language="python"><span class="hljs-comment">#&nbsp;获取&nbsp;shape</span>
shape&nbsp;=&nbsp;df_rating.shape
<span class="hljs-comment">#&nbsp;从shape&nbsp;获取&nbsp;行数</span>
row_count&nbsp;=&nbsp;shape[<span class="hljs-number">0</span>]
<span class="hljs-comment">#&nbsp;用于临时存放每一行&nbsp;level&nbsp;的信息</span>
levels&nbsp;=&nbsp;[]
<span class="hljs-comment">#&nbsp;用一个循环，来对每一行都进行处理</span>
<span class="hljs-keyword">for</span>&nbsp;i&nbsp;<span class="hljs-keyword">in</span>&nbsp;range(<span class="hljs-number">0</span>,&nbsp;row_count):
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">#&nbsp;获取当前行的评分</span>
&nbsp;&nbsp;&nbsp;&nbsp;rating&nbsp;=&nbsp;df_rating.loc[i,&nbsp;<span class="hljs-string">"rating"</span>]
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">#&nbsp;去除&nbsp;分&nbsp;字，方便比较大小</span>
&nbsp;&nbsp;&nbsp;&nbsp;rating&nbsp;=&nbsp;rating.replace(<span class="hljs-string">"分"</span>,&nbsp;<span class="hljs-string">""</span>)
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">#&nbsp;计算评级结果，并添加到&nbsp;levels&nbsp;列表</span>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">if</span>&nbsp;rating&nbsp;&lt;&nbsp;<span class="hljs-string">"2.0"</span>:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;levels.append(<span class="hljs-string">"低"</span>)
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">elif</span>&nbsp;rating&nbsp;&lt;&nbsp;<span class="hljs-string">"4.0"</span>:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;levels.append(<span class="hljs-string">"中"</span>)
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">else</span>:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;levels.append(<span class="hljs-string">"高"</span>)
<span class="hljs-comment">#&nbsp;将&nbsp;levels&nbsp;构造成&nbsp;Series，并通过列索引&nbsp;level,&nbsp;添加到&nbsp;DataFrame</span>
df_rating[<span class="hljs-string">"level"</span>]&nbsp;=&nbsp;pd.Series(levels)
<span class="hljs-comment">#&nbsp;查看</span>
df_rating
</code></pre>
<p data-nodeid="17001" class="te-preview-highlight">执行之后，输出：<br>
<img src="https://s0.lgstatic.com/i/image6/M01/3F/36/Cgp9HWCc5v-ALrE8AAHGkz4dB2o796.png" alt="Drawing 13.png" data-nodeid="17006"></p>

---

### 精选评论


