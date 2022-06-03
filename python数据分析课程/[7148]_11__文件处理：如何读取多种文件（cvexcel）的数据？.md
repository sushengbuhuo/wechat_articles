<p data-nodeid="16075" class="">从今天开始，我们进入了一个新的部分：使用 pandas 进行数据处理。在上一个模块我们学习了爬虫技术，并学会了怎么将数据从网页中抓取出来保存成 csv 数据集。</p>
<p data-nodeid="16076">在有了数据集之后，接下来我们就开始学习怎么把数据集的内容加载到 Python 中。虽然我们在上一个模块学过简单的读取 csv 的文件内容。</p>
<p data-nodeid="16077">但是存在两个问题：</p>
<ol data-nodeid="16078">
<li data-nodeid="16079">
<p data-nodeid="16080">只能读取 csv 文件，但数据分析的数据除了可能来自 csv，也可能来自 Excel，甚至可以来自 html 的表格。</p>
</li>
<li data-nodeid="16081">
<p data-nodeid="16082">读取到的结果一般是字典列表，并不利于分析，比如虽然我们每个字典就代表一行记录，但一旦我们想拿某一列的数据的时候就会非常复杂。</p>
</li>
</ol>
<p data-nodeid="16083">Python 作为数据分析领域的头号种子选手，自然不会只有 csv 模块这样的初级工具。这个部分我们将会学习表格类型的大数据处理神器：pandas.</p>
<p data-nodeid="16084">pandas 不仅可以从多种不同的文件格式读取数据，还有各种各样的数据处理的功能。可以说学好了pandas，就基本已经算踏上了数据分析之路。话不多说，我们这就开始 pandas 之旅。</p>
<h3 data-nodeid="16085">课前准备：安装 pandas 工具包</h3>
<p data-nodeid="16086">和前面的课程一致，我们第一步需要安装 pandas 工具包。打开开始菜单 → Anaconda3 → Anaconda Prompt， 并输入 conda install pandas 回车执行， 如下图所示。</p>
<p data-nodeid="16087"><img src="https://s0.lgstatic.com/i/image6/M01/3D/BE/CioPOWCWJUGAAuSkAAENUnrgPlY677.png" alt="Drawing 0.png" data-nodeid="16270"></p>
<p data-nodeid="16088">输入 y 确认安装，安装完毕后关闭该窗口。</p>
<p data-nodeid="16089">到课程目录，新建文件夹 chapter11。之后打开 VS code，选择文件 → 打开文件夹，选择打开刚才创建的 chapter11 文件夹。</p>
<p data-nodeid="16090">打开文件夹之后，创建新的 Notebook，并保存到刚才我们创建的 chapter11 文件夹中，并命名为 chapter11.ipynb。</p>
<p data-nodeid="16091">在第一个 Cell 中，导入 pandas。这次为了在后续调用 pandas 的函数方便，我们给它起一个别名：pd。import 语句中，在模块名后面 跟 as 就可以给导入的模块起一个别名，如下所示。</p>
<pre class="lang-python" data-nodeid="16092"><code data-language="python"><span class="hljs-keyword">import</span> pandas <span class="hljs-keyword">as</span> pd
</code></pre>
<p data-nodeid="16093">运行之后如果没有报错，说明 pandas 已经成功安装。</p>
<h3 data-nodeid="16094">使用 pandas 读取 csv 文件</h3>
<p data-nodeid="16095">首先我们来学习如何使用 pandas 来读取 csv 文件。</p>
<p data-nodeid="16096">pandas 模块提供了一个 read_ csv 的方法，可以直接读取 csv 文件，并返回一个 DataFrame 对象。DataFrame 对象是 pandas 模块的核心，pandas 的所有表格都是通过 DataFrame 对象来存储的，并且 DataFrame 还提供了非常多查看数据、修改数据的方法。我们在之后的课程中会逐渐学习 DataFrame 的用法。</p>
<p data-nodeid="16097">现在你只需要知道，pandas 可以直接从一个 csv 文件中，将数据读到 Python 中，并且以DataFrame 对象的形式返回，我们拿到这个对象就可以查看其中的数据就可以了。</p>
<h4 data-nodeid="16098">实战 read_ csv</h4>
<p data-nodeid="16099">我们来具体演练一下这个过程。首先我们将上一讲收集到的国产电视剧数据集 tv_rating. csv 拷贝到 chapter11 文件夹中。</p>
<p data-nodeid="16100">新建 Cell， 输入如下的代码。</p>
<pre class="lang-python" data-nodeid="16101"><code data-language="python"><span class="hljs-comment">#&nbsp;使用&nbsp;pandas&nbsp;模块的&nbsp;read_ csv&nbsp;函数，读取&nbsp;csn&nbsp;文件。并将结果存在&nbsp;df_rating&nbsp;变量中</span>
df_rating&nbsp;=&nbsp;pd.read_ csv(<span class="hljs-string">"tv_rating. csv"</span>)
<span class="hljs-comment">#&nbsp;打印&nbsp;df_rating&nbsp;变量</span>
print(<span class="hljs-string">"df_rating:"</span>)
print(df_rating)
<span class="hljs-comment">#&nbsp;打印&nbsp;df_rating&nbsp;变量的类型</span>
print(<span class="hljs-string">"df_rating&nbsp;type:"</span>)
print(type(df_rating))
</code></pre>
<p data-nodeid="16102">运行之后输出如下所示。(为了表格类的数据看着好看一些，所以这类数据我都截图展示)。</p>
<p data-nodeid="16103"><img src="https://s0.lgstatic.com/i/image6/M01/3D/B6/Cgp9HWCWJUyADMoLAAKPt-W-zEM315.png" alt="Drawing 1.png" data-nodeid="16292"></p>
<p data-nodeid="16104">从上面的输出中可以看到，df_rating 变量中包含了我们 csv 文件中的所有数据，并且还有形状的描述：3600 行 x 3列，这个也和我们下载的数据一致。通过打印 df_rating 的类型，可以看到 df_rating 的类型就是我们上文提到的 DataFrame。</p>
<h4 data-nodeid="16105">更好看的表格</h4>
<p data-nodeid="16106">DataFrame 很强大，它甚至针对 notebook 有专门优化。我们之前学习过，当一个 Cell 的最后一行是一个变量时，那 notebook 就会将这个变量打印出来。比如如下的代码：</p>
<pre class="lang-python" data-nodeid="16107"><code data-language="python">a = <span class="hljs-number">3</span>
b = <span class="hljs-number">4</span> + a
a
</code></pre>
<p data-nodeid="16108">或者</p>
<pre class="lang-python" data-nodeid="16109"><code data-language="python">a
</code></pre>
<p data-nodeid="16110">这样的代码，即便没有任何的 print 语句，但因为满足 cell 最后一行是一个变量条件，那 notebook 都会打印出这个变量，也就是 a 的值。</p>
<p data-nodeid="16111">回到 DataFrame， 当我们不是直接用 print 打印它，而是把 DataFrame 变量放在 Cell 的末尾时， notebook 就会用一种更好看的格式来打印它。我们马上来试一下，直接新建一个 Cell，输入如下的代码运行。</p>
<pre class="lang-python" data-nodeid="16112"><code data-language="python">df_rating
</code></pre>
<p data-nodeid="16113">输出</p>
<p data-nodeid="16114"><img src="https://s0.lgstatic.com/i/image6/M01/3D/BE/CioPOWCWJViATNS6AAIUgxWwN2o307.png" alt="Drawing 2.png" data-nodeid="16308"></p>
<p data-nodeid="16115">可以看到这一次的格式可比上一次好看多了，更像一个表格，对应的也更加整齐。DataFrame 的常见操作我们下一讲会具体展开介绍。</p>
<h3 data-nodeid="16116">使用 pandas 读取 excel 文件</h3>
<p data-nodeid="16117">在 Python 还没有兴起之前，大量的数据分析是通过 Excel 完成的。这也造就了在很多传统行业中，还有大量的数据是保存在 Excel 中，所以读取 Excel 也是进行分析也是 Python 数据分析领域的常见任务。</p>
<p data-nodeid="16118">Excel 的 .xls/.xlsx 文件格式是微软针对表格开发的，只能使用 Excel 来打开，比如用记事本打开往往会看到有乱码。那 Python 是怎么读取 Excel 里面的内容呢？那自然是我们本模块的 Super Star：pandas。</p>
<p data-nodeid="16119">类似 csv 的读取，pandas 也提供了 read_excel 函数来实现读取 excel 文件中的内容，但是使用方法比 read_ csv 稍微复杂一些。</p>
<p data-nodeid="16120">接下来我们通过一个小实战来学习 read_excel 使用。</p>
<h4 data-nodeid="16121">（1）准备测试数据</h4>
<p data-nodeid="16122">我们之前做的数据都是 csv 格式的。我们现在先来制作一个简单的 excel 文件，用来测试我们后面的代码。</p>
<p data-nodeid="16123">打开 Excel ，将第一个表格（sheet）的名字改为：基本信息，并复制添加下述内容</p>
<p data-nodeid="16530" class=""><img src="https://s0.lgstatic.com/i/image6/M00/3E/49/Cgp9HWCY25mAPoQKAABMElc0YNA061.png" alt="1.png" data-nodeid="16533"></p>

<p data-nodeid="16153">添加完后的 Excel 如下所示</p>
<p data-nodeid="16154"><img src="https://s0.lgstatic.com/i/image6/M01/3D/B6/Cgp9HWCWJWWANsA3AADm8AXpScQ480.png" alt="Drawing 3.png" data-nodeid="16343"></p>
<p data-nodeid="16155">然后，点击下面的 +号，点击新建一个表格，并命名为“绩效”，然后复制粘贴以下内容。</p>
<p data-nodeid="17362" class="te-preview-highlight"><img src="https://s0.lgstatic.com/i/image6/M00/3E/49/Cgp9HWCY26eAALxwAABK5F5N0L8191.png" alt="2.png" data-nodeid="17365"></p>

<p data-nodeid="16180">添加之后的 Excel 界面如下所示。</p>
<p data-nodeid="16181"><img src="https://s0.lgstatic.com/i/image6/M00/3D/BE/CioPOWCWJb6AEoVdAADv603fm-E192.png" alt="Drawing 4.png" data-nodeid="16360"></p>
<p data-nodeid="16182">保存 Excel 到之前我们建的 chapter11 目录中，并命名为 info.xlsx。</p>
<h4 data-nodeid="16183">（2）读取数据</h4>
<p data-nodeid="16184">数据准备完毕了，现在我们来读取我们刚才创建的表格。形式类似刚才的 read_ csv， 你可以先尝试思考一下自己写，然后继续往下看。</p>
<p data-nodeid="16185">新建 Cell ，输入如下的代码。</p>
<pre class="lang-python" data-nodeid="16186"><code data-language="python"><span class="hljs-comment">#&nbsp;使用&nbsp;read_excel&nbsp;函数，读取&nbsp;info.xlsx&nbsp;的内容并存储在&nbsp;df_info&nbsp;变量中</span>
df_info&nbsp;=&nbsp;pd.read_excel(<span class="hljs-string">"info.xlsx"</span>)
<span class="hljs-comment">#&nbsp;不用&nbsp;print，直接将&nbsp;df_info&nbsp;放在最后一行，让notebook用表格形式打印</span>
df_info
</code></pre>
<p data-nodeid="16187" class="">执行之后，输出如下。<br>
<img src="https://s0.lgstatic.com/i/image6/M00/3D/BE/CioPOWCWJcaANQkrAAAxyK7fFMY251.png" alt="Drawing 5.png" data-nodeid="16371"></p>
<p data-nodeid="16188">可以看到，Excel 中的数据被成功的打印了出来，和 read_ csv 一样，read_excel 返回的也是一个 DataFrame。</p>
<p data-nodeid="16189">不过内容虽然打印出来了，但是只打印出了第一个表格，也就是“基本信息”这个表格，我们后面添加的“绩效”表格并没有打印出来。这是 pandas 的机制导致的，read_excel 默认读取 excel 文件中的一个表格。</p>
<p data-nodeid="16190">一个 Excel 中包含多个表格还是很常见的，pandas 不可能坐视不理，如何读取更多的表格呢？我们进入下一个步骤。</p>
<h4 data-nodeid="16191">（3）读取不同的表格</h4>
<p data-nodeid="16192">read_excel 比 read_ csv 复杂的地方就在于，read_excel 支持非常多的参数。比如要实现读取后面的表格，我们只需要给 read_excel 函数的 sheet_name 参数赋值即可。</p>
<p data-nodeid="16193">新建 Cell，输入下面的代码。</p>
<pre class="lang-python" data-nodeid="16194"><code data-language="python"><span class="hljs-comment">#&nbsp;使用&nbsp;read_excel&nbsp;函数读取&nbsp;info.xlsx&nbsp;文件里的&nbsp;“绩效”&nbsp;这个表格</span>
<span class="hljs-comment">#&nbsp;并将结果存在&nbsp;df_perf&nbsp;变量中</span>
df_perf&nbsp;=&nbsp;pd.read_excel(<span class="hljs-string">"info.xlsx"</span>,&nbsp;sheet_name=<span class="hljs-string">"绩效"</span>)
<span class="hljs-comment">#&nbsp;让notebook&nbsp;打印&nbsp;df_perf&nbsp;变量</span>
df_perf
</code></pre>
<p data-nodeid="16195">输出如下所示。</p>
<p data-nodeid="16196"><img src="https://s0.lgstatic.com/i/image6/M01/3D/B6/Cgp9HWCWJc6ABaWsAAAz1xFmzUw736.png" alt="Drawing 6.png" data-nodeid="16397"></p>
<p data-nodeid="16197">可以看到，这次输出的就是我们增加的“绩效”表格中的内容。</p>
<p data-nodeid="16198">简单来说，<strong data-nodeid="16408">我们可以在 read_excel 中，通过给 sheet_name 赋值来决定要加载文件哪个表格，如果不指定，pandas 则默认加载第一个表格</strong>。</p>
<h4 data-nodeid="16199">（4）选择性读取</h4>
<p data-nodeid="16200">有时候， excel 文件的数据很多，全部加载到 Python 中可能会卡，而且有时候我们只对其中某几列感兴趣，全部加载显示也不容易看。read_excel 提供了 usecols 参数，可以指定要加载哪几列。</p>
<p data-nodeid="16201">举个例子，刚才的“绩效”表格，我们对上期考核结果不感兴趣，只想加载姓名和绩效考核这两列的内容。那我们可以这么做，新建 Cell，输入如下代码。</p>
<pre class="lang-python" data-nodeid="16202"><code data-language="python"><span class="hljs-comment">#&nbsp;使用&nbsp;read_excel&nbsp;函数读取&nbsp;info.xlsx&nbsp;中的&nbsp;绩效&nbsp;表格</span>
<span class="hljs-comment">#&nbsp;并只读取&nbsp;A&nbsp;B两行，并将结果存到&nbsp;df_perf1&nbsp;变量中</span>
df_perf1&nbsp;=&nbsp;pd.read_excel(<span class="hljs-string">"info.xlsx"</span>,&nbsp;sheet_name=<span class="hljs-string">"绩效"</span>,&nbsp;usecols=<span class="hljs-string">"A,B"</span>)
<span class="hljs-comment">#&nbsp;让&nbsp;notebook&nbsp;打印&nbsp;df_perf1&nbsp;变量</span>
df_perf1
</code></pre>
<p data-nodeid="16203">执行之后，输出结果可以看到，我们已经成功实现了只加载前两列的内容。</p>
<p data-nodeid="16204"><img src="https://s0.lgstatic.com/i/image6/M00/3D/BF/CioPOWCWJdmARpP5AAAlohezKM8738.png" alt="Drawing 7.png" data-nodeid="16417"></p>
<p data-nodeid="16205">在上面的代码里，我们通过字母 A 和 B 指定了加载第一列和第二列。字母和列的对应关系其实就是 Excel 里面的对应关系。如下图所示。</p>
<p data-nodeid="16206"><img src="https://s0.lgstatic.com/i/image6/M01/3D/B6/Cgp9HWCWJd6AIRR1AAEO8tMU3eU810.png" alt="Drawing 8.png" data-nodeid="16421"></p>
<p data-nodeid="16207">至此，我们学习完了基本的读取 excel 文件的操作。</p>
<h3 data-nodeid="16208">使用 pandas 读取 html 文件</h3>
<p data-nodeid="16209">有的时候数据并不是整理好的 csv 表格或者 Excel 表格，而是以网页中的表格的形式存在，最常见的就是各类股票财经网站，比如像同花顺的股票涨跌幅数据中心：<a href="http://data.10jqka.com.cn/market/zdfph/?fileGuid=xxQTRXtVcqtHK6j8" data-nodeid="16427">http://data.10jqka.com.cn/market/zdfph/</a>。</p>
<p data-nodeid="16210"><img src="https://s0.lgstatic.com/i/image6/M00/3D/B6/Cgp9HWCWJeiAZkmxAAbhDyca7tw465.png" alt="Drawing 9.png" data-nodeid="16431"></p>
<p data-nodeid="16211">或者像招行银行的外汇行情页面，如下所示。</p>
<p data-nodeid="16212"><img src="https://s0.lgstatic.com/i/image6/M00/3D/B6/Cgp9HWCWJe-AXZ3bAAY3rmneDJg833.png" alt="Drawing 10.png" data-nodeid="16435"></p>
<p data-nodeid="16213">如果我们希望将这些网页中的表格“导入”到 Python 进行处理，那自然也是可以的。根据我们上一个部分学习的爬虫技术，我们只需要将这个页面的 html 下载下来，然后用 BeautifulSoup 分析表格的标签结构，然后把内容一行一行的提取出来，再一步一步拆分成列。</p>
<p data-nodeid="16214">做是可以做，但只听这个流程，只看这个复杂的页面，都让人觉得工作量很大。而对于提取网页中的表格，其实存在一个非常简单的方法：使用强大的 pandas。</p>
<p data-nodeid="16215">和 read_ csv、read_excel 类似，pandas 也提供了一个 read_html 的方法，来<strong data-nodeid="16449">智能的提取网页中的所有表格</strong>，并以 DataFrame 列表的形式返回，一个表格对应一个 DataFrame。看到这里，是否有感触到 pandas 的强大之处？</p>
<p data-nodeid="16216">我们还是通过一个简单的小例子来学习 read_html 方法的使用。我们以刚才举的招商银行外汇行情的页面为例，尝试在 Python 中加载该网页中表格的数据。</p>
<h4 data-nodeid="16217">（1）准备网页</h4>
<p data-nodeid="16218">首先要做的第一件事，就是要拿到网页的内容。在第 07 讲中，我们已经写过了一个拿网页内容的函数。</p>
<p data-nodeid="16219">新建 Cell，将第 07 讲的 download_content 函数先搬过来，别忘记在开头加上导入 urllib3的语句，代码如下所示。</p>
<pre class="lang-python" data-nodeid="16220"><code data-language="python"><span class="hljs-keyword">import</span>&nbsp;urllib3
<span class="hljs-function"><span class="hljs-keyword">def</span>&nbsp;<span class="hljs-title">download_content</span>(<span class="hljs-params">url</span>):</span>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">#&nbsp;创建一个&nbsp;PoolManager&nbsp;对象，命名为&nbsp;http</span>
&nbsp;&nbsp;&nbsp;&nbsp;http&nbsp;=&nbsp;urllib3.PoolManager()
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">#&nbsp;调用&nbsp;http&nbsp;对象的&nbsp;request&nbsp;方法，第一个参数传一个字符串&nbsp;"GET"</span>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">#&nbsp;第二个参数则是要下载的网址，也就是我们的&nbsp;url&nbsp;变量</span>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">#&nbsp;request&nbsp;方法会返回一个&nbsp;HTTPResponse&nbsp;类的对象，我们命名为&nbsp;response</span>
&nbsp;&nbsp;&nbsp;&nbsp;response&nbsp;=&nbsp;http.request(<span class="hljs-string">"GET"</span>,&nbsp;url)
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">#&nbsp;获取&nbsp;response&nbsp;对象的&nbsp;data&nbsp;属性，存储在变量&nbsp;response_data&nbsp;中</span>
&nbsp;&nbsp;&nbsp;&nbsp;response_data&nbsp;=&nbsp;response.data
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">#&nbsp;调用&nbsp;response_data&nbsp;对象的&nbsp;decode&nbsp;方法，获得网页的内容，存储在&nbsp;html_content&nbsp;</span>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">#&nbsp;变量中</span>
&nbsp;&nbsp;&nbsp;&nbsp;html_content&nbsp;=&nbsp;response_data.decode()
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">return</span>&nbsp;html_content
html_content&nbsp;=&nbsp;download_content(<span class="hljs-string">"http://fx.cmbchina.com/Hq/"</span>)
</code></pre>
<p data-nodeid="16221">执行上述代码之后，网页内容就已经存储在 html_content 变量中。</p>
<h4 data-nodeid="16222">（2）读取数据</h4>
<p data-nodeid="16223">在准备好了网页的内容之后，我们就可以调用 read_html 函数来获取表格了。</p>
<p data-nodeid="16224">新建 Cell，输入如下代码。</p>
<pre class="lang-python" data-nodeid="16225"><code data-language="python"><span class="hljs-comment">#&nbsp;调用&nbsp;read_html&nbsp;函数，传入网页的内容，并将结果存储在&nbsp;cmb_table_list&nbsp;中</span>
<span class="hljs-comment">#&nbsp;read_html&nbsp;函数返回的是一个&nbsp;DataFrame&nbsp;的list</span>
cmb_table_list&nbsp;=&nbsp;pd.read_html(html_content)
<span class="hljs-comment">#&nbsp;打印&nbsp;list&nbsp;的长度，看看抽取出了几个表格</span>
print(len(cmb_table_list))
</code></pre>
<p data-nodeid="16226">执行代码，输出结果为 2。这说明找到了两个表格，但我们回过头去看网页，主体应该只有一个表格。这种情况还是比较常见的，多半是网页在一些<strong data-nodeid="16475">不是表格的元素也使用了表格的标签</strong>，导致 pandas 识别多了一个，遇到这样的情况我们只需要<strong data-nodeid="16476">逐一查看返回的 DataFrame 列表</strong>，找到我们要的即可。</p>
<p data-nodeid="16227"><img src="https://s0.lgstatic.com/i/image6/M00/3D/BF/CioPOWCWJf6AJeEpAAY3rmneDJg801.png" alt="Drawing 11.png" data-nodeid="16479"></p>
<p data-nodeid="16228">现在我们来从列表中找出我们要的表格，首先查看第一个 DataFrame。</p>
<p data-nodeid="16229">新建 Cell， 输入以下代码并运行。</p>
<pre class="lang-python" data-nodeid="16230"><code data-language="python"><span class="hljs-comment">#&nbsp;直接写变量，利用&nbsp;notebook&nbsp;的特性打印表格</span>
cmb_table_list[<span class="hljs-number">0</span>]
</code></pre>
<p data-nodeid="16231">执行后，输出如下：</p>
<p data-nodeid="16232"><img src="https://s0.lgstatic.com/i/image6/M00/3D/B6/Cgp9HWCWJgyAQv1mAAAhvorP4NA771.png" alt="Drawing 12.png" data-nodeid="16485"></p>
<p data-nodeid="16233">很明显，这不是我们要的表格，现在我们看第二个。</p>
<p data-nodeid="16234">新建 Cell，输入如下的代码。</p>
<pre class="lang-python" data-nodeid="16235"><code data-language="python">cmb_table_list[<span class="hljs-number">1</span>]
</code></pre>
<p data-nodeid="16236">执行之后，输出如下所示。<br>
<img src="https://s0.lgstatic.com/i/image6/M00/3D/BF/CioPOWCWJiCAEwgHAAFrcarzvm4465.png" alt="Drawing 13.png" data-nodeid="16492"></p>
<p data-nodeid="16237">很明显，这个就是我们要的表格了。可以看到我们在招行官网上看到的汇率表格已经完整的被加载到了 pandas 的 DataFrame 中，并且能够以表格的形式打印出来。是不是感觉到非常神奇？</p>
<p data-nodeid="16238">如果我们用 BeautifulSoup 来解析这个网页然后提取出表格的内容，恐怕代码都要写大几十行，而 pandas 却一个函数搞定了。</p>
<h3 data-nodeid="16239">小结</h3>
<p data-nodeid="16240">至此，我们从各种文件读取数据生成 DataFrame 的课程就学习完毕了。下一讲我们将会学习拿到 DataFrame 后，我们如何愉快的操作和查看里面的数据。</p>
<p data-nodeid="16241">回顾一下今天学习的内容，我们可以：</p>
<ul data-nodeid="16242">
<li data-nodeid="16243">
<p data-nodeid="16244">通过 read_ csv 函数将 csv 读取到 pandas 的 DataFrame 对象；</p>
</li>
<li data-nodeid="16245">
<p data-nodeid="16246">通过 read_excel 函数将 excel 文件读取到 DataFrame，并且可以通过 cheet_name 参数指定要读取哪个表，以及通过 use_cols 参数来指定要读取哪几列；</p>
</li>
<li data-nodeid="16247">
<p data-nodeid="16248">通过 read_html 函数将 html 内容中的表格提取为一个DataFrame 的列表，通过逐一查看来确定哪个是我们想要的。</p>
</li>
</ul>
<p data-nodeid="16249"><strong data-nodeid="16514">课后练习</strong></p>
<p data-nodeid="16250">尝试加载人民银行的2020金融市场报表数据(<a href="http://www.pbc.gov.cn/eportal/fileDir/defaultCurSite/resource/cms/2021/01/2021011818262828764.htm?fileGuid=xxQTRXtVcqtHK6j8" data-nodeid="16518">http://www.pbc.gov.cn/eportal/fileDir/defaultCurSite/resource/cms/2021/01/2021011818262828764.htm</a>)</p>
<p data-nodeid="16251">提示：该网页需要使用动态内容下载技术 selenium。</p>
<p data-nodeid="16252">快来动手操作下！操作完再看答案~</p>
<hr data-nodeid="16253">
<p data-nodeid="16254">答案：</p>
<pre class="lang-python" data-nodeid="16255"><code data-language="python">url=&nbsp;<span class="hljs-string">"http://www.pbc.gov.cn/eportal/fileDir/defaultCurSite/resource/cms/2021/01/2021011818262828764.htm"</span>
<span class="hljs-keyword">from</span>&nbsp;selenium&nbsp;<span class="hljs-keyword">import</span>&nbsp;webdriver
brow&nbsp;=&nbsp;webdriver.Chrome()
brow.get(url)
eco_content&nbsp;=&nbsp;brow.page_source
<span class="hljs-comment">#&nbsp;print(eco_content)</span>
df_list&nbsp;=&nbsp;pd.read_html(eco_content)
print(len(df_list))
</code></pre>
<p data-nodeid="16256">输出 1，代表只发现一个表格。直接在新的 Cell 里面输出列表的第一个元素即可</p>
<pre class="lang-python" data-nodeid="16257"><code data-language="python">df_list[<span class="hljs-number">0</span>]
</code></pre>
<p data-nodeid="16258" class="">输出:<br>
<img src="https://s0.lgstatic.com/i/image6/M01/3D/B6/Cgp9HWCWJi2ALDmEAALrDxDzE3Y335.png" alt="Drawing 14.png" data-nodeid="16529"></p>

---

### 精选评论

##### **宇：
> 加油，加油，刚白得!

##### *路：
> 感觉很精彩，意犹未尽

