<p data-nodeid="1757" class="">“工欲善其事，必先利其器。”在课程正式开始之前，我们先搭建一套高效的 Python 工作环境为后续数据分析做准备。</p>
<p data-nodeid="1758">关于高效作业，对于需要编写 Python 代码进行数据分析的工作而言，主要涉及两个方面。</p>
<p data-nodeid="1759"><strong data-nodeid="1909">1. 一款具备强大的自动完成和错误提示的开发工具。</strong></p>
<p data-nodeid="1760">Python 丰富的函数库和组件库是这门语言强大的核心原因，但我们不可能去记忆所有的方法名和参数名，往往只能记住一些常用的或者某个方法开头的几个字母。这个时候<strong data-nodeid="1915">一个好的开发工具就需要能聪明地“猜”出你想输入的代码</strong>，并给出候选列表方便你选择（类似于输入法的字词提示功能）。</p>
<p data-nodeid="1761">另外，<strong data-nodeid="1921">当你输入错误的时候，这个工具能够提示你具体是哪里错了，建议改成什么，从而大幅提升编写效率</strong>。在别人还在查到底是哪个单词拼错了导致代码跑不起来的时候，你已经写完一个完整的模块了。</p>
<p data-nodeid="1762"><strong data-nodeid="1927">2. 掌握快捷键。</strong></p>
<p data-nodeid="1763">Python 数据分析需要边写边看结果，甚至每写两行代码就需要点击运行、新建文本段落、代码段落等操作。所以熟练地掌握快捷键，可以使绝大多数的操作都不需要鼠标，手不用离开键盘就能完成，起到事半功倍的效果。</p>
<h3 data-nodeid="1764">说干就干，Let's hack!</h3>
<p data-nodeid="1765">接下来，我就先带你配置一套比传统方式更高效的数据分析开发工具，而快捷键则会在之后的教学过程一步步教给大家。</p>
<p data-nodeid="1766">整个配置过程相比传统的环境安装稍微多了几步，不过并不复杂，你只需要跟着一步一步操作就可以。</p>
<blockquote data-nodeid="1767">
<p data-nodeid="1768">本课时搭建环境的版本说明如下：<br>
Anaconda3.0<br>
VS Code 1.51.1<br>
实际并无太多版本限制，你安装最新版即可。</p>
</blockquote>
<h4 data-nodeid="1769">第一步，数据科学增强版的 Python 环境：Anaconda</h4>
<p data-nodeid="1770">Anaconda 是一个 Python 数据科学工具包，里面包含了 Python 做数据计算最常用的库和工具，属于必装软件。目前它已经非常成熟，并且整套 Anaconda 可以免费提供给个人使用。</p>
<p data-nodeid="1771"><strong data-nodeid="1961">1</strong>. 用浏览器访问 Anaconda 的个人版页面：<a href="https://www.anaconda.com/products/individual?fileGuid=xxQTRXtVcqtHK6j8" data-nodeid="1950">h</a><a href="https://www.anaconda.com/products/individual?fileGuid=xxQTRXtVcqtHK6j8" data-nodeid="1953">ttps://www.anac</a><a href="https://www.anaconda.com/products/individual?fileGuid=xxQTRXtVcqtHK6j8" data-nodeid="1956">on</a><a href="https://www.anaconda.com/products/individual?fileGuid=xxQTRXtVcqtHK6j8" data-nodeid="1959">da.com/products/individual</a> ，点击 Download，页面会自动跳转到具体的下载页面，如图所示：</p>
<p data-nodeid="1772"><img src="https://s0.lgstatic.com/i/image6/M01/2D/6F/Cgp9HWBmjziAHkoCAAJzVFPWD-c336.png" alt="Drawing 0.png" data-nodeid="1964"></p>
<p data-nodeid="1773"><strong data-nodeid="1969">2</strong>. 根据自己的设备类型 （Mac/Windows），选择合适的安装包版本。无论 Windows 还是Mac， 都选择 Graphical Installer，它代表图形化的安装器，之后更易于使用。</p>
<blockquote data-nodeid="1774">
<p data-nodeid="1775">本篇教程后续步骤以 Windows 为例。</p>
</blockquote>
<p data-nodeid="1776"><strong data-nodeid="1975">3</strong>. 下载之后双击安装包进行安装（如图所示），直接点击 Next。</p>
<p data-nodeid="1777"><img src="https://s0.lgstatic.com/i/image6/M00/2D/77/CioPOWBmj1OAPltdAAJG0cCuo4w472.png" alt="Drawing 1.png" data-nodeid="1978"></p>
<p data-nodeid="1778"><strong data-nodeid="1983">4</strong>. 接下来就是使用协议界面，点击 I Agree，代表同意使用协议。</p>
<p data-nodeid="1779"><img src="https://s0.lgstatic.com/i/image6/M00/2D/77/CioPOWBmj1mAOKfCAAM0jYlBpcU374.png" alt="Drawing 2.png" data-nodeid="1986"></p>
<p data-nodeid="1780"><strong data-nodeid="1991">5</strong>. 之后连续 Next，可以看到选择安装位置的界面，如果没有特殊的需求，直接默认位置就好，继续点击 Next。</p>
<p data-nodeid="1781"><img src="https://s0.lgstatic.com/i/image6/M00/2D/6F/Cgp9HWBmj1-AZ7mOAAH8fGuG76g018.png" alt="Drawing 3.png" data-nodeid="1994"></p>
<p data-nodeid="1782"><strong data-nodeid="2001">6</strong>. 最后一个配置界面是高级选项，不用更改，直接点击 Install，等待 2~3 分钟之后，即可完成安装。</p>
<p data-nodeid="1783">安装完毕之后，可以从程序中找到 Anaconda Navigator，点击打开就可以看到整套 Anaconda3 的所有工具（如下图所示）：</p>
<p data-nodeid="1784"><img src="https://s0.lgstatic.com/i/image6/M00/2D/77/CioPOWBmj2mAY44ZAAJ4bjvt15I883.png" alt="Drawing 4.png" data-nodeid="2005"></p>
<p data-nodeid="1785">其中 Notebook 是数据分析应用范围最广泛的工具，也是本次课程的主力工具，但它却不是一款足够有效率的工具，因为它缺乏智能的代码输入联想、自动完成和错误提示。而有效率的分析师是不会容忍自己用“记事本”写代码的。</p>
<p data-nodeid="1786">所以，接下来，我会带你在自己的电脑中配置一个智能、强大的 Notebook（此时安装好的Anaconda3 页面先不关闭）。</p>
<h4 data-nodeid="1787">第二步，飞一般的代码编辑器：VS Code</h4>
<p data-nodeid="1788">VS Code（ Visual Studio Code），是微软开发的跨平台代码编辑器，靠着其强大的插件生态，目前已经成为全球最流行的代码编辑器。本次我们就通过 VS Code，来解决 Notebook 开发效率的问题。</p>
<p data-nodeid="1789">首先按照以下的步骤安装和配置 VS Code。</p>
<p data-nodeid="1790"><strong data-nodeid="2019">1</strong>. 下载：用浏览器访问<a href="https://code.visualstudio.com/?fileGuid=xxQTRXtVcqtHK6j8" data-nodeid="2017">https://code.visualstudio.com/</a>，网页会直接识别当前的操作系统，直接点击下载按钮，下载安装包。</p>
<p data-nodeid="1791"><strong data-nodeid="2024">2</strong>. 安装：下载完毕后，双击安装包进行安装，全部默认配置即可。</p>
<p data-nodeid="1792"><strong data-nodeid="2029">3</strong>. 安装中文语言包【可选，习惯英文的同学可以跳过】：启动 VS Code，进入插件 Tab（左侧边栏最后下方的图标），输入 【Chinese】，出现的第一个插件，点击 Install 安装。安装完成后，重启 VS Code 即可生效。</p>
<p data-nodeid="1793"><img src="https://s0.lgstatic.com/i/image6/M00/2D/77/CioPOWBmj3GAU1p2AAD2IWnRzOU216.png" alt="Drawing 5.png" data-nodeid="2032"></p>
<p data-nodeid="1794"><strong data-nodeid="2037">4</strong>. 安装 Python 插件：依旧是在插件面板，输入 【Python】，安装列表中的第一个插件。</p>
<p data-nodeid="1795"><img src="https://s0.lgstatic.com/i/image6/M00/2D/6F/Cgp9HWBmj4eAIa0-AAB94MABrDY329.png" alt="Drawing 6.png" data-nodeid="2040"></p>
<p data-nodeid="1796">至此，基础的 VS Code 环境已经配置完毕，在下一步我们会开始用 VS Code 编写Python 代码。</p>
<h4 data-nodeid="1797">第三步，配置 VS Code 使用 Anaconda 的Python环境</h4>
<p data-nodeid="1798">现在，我们开始实际地玩一玩 VS Code。</p>
<p data-nodeid="1799">打开 VS Code，选择【文件】-【新建文件】，会建立一个默认的文本文件，按 CTRL +s 保存，文件名为【hello.py】。</p>
<blockquote data-nodeid="1800">
<p data-nodeid="1801">后缀名一定要是 .py，因为 VS Code 要根据文件的后缀名来匹配合适的工具链。</p>
</blockquote>
<p data-nodeid="1802">保存之后，如果 VS Code 识别到 Python 文件，我们上一步安装的 Python 插件就会开始工作，寻找本机的Python 环境，结果会展示在下方的状态栏上。</p>
<p data-nodeid="1803"><img src="https://s0.lgstatic.com/i/image6/M00/2D/77/CioPOWBmj46Ac9KZAABFRVP-_yA643.png" alt="Drawing 7.png" data-nodeid="2049"></p>
<p data-nodeid="1804">状态栏上的是 Python 3.8.5 64-bit(conda)，说明目前 VS Code 已经在使用我们第一步 Anaconda 安装的 Python 环境。如果不是，可以点击这行字，在弹出的列表中选择带 Conda 字样的Python 环境。</p>
<blockquote data-nodeid="1805">
<p data-nodeid="1806">Anaconda的 Python环境包含了丰富的科学计算的库，所以是做数据分析的首选。</p>
</blockquote>
<p data-nodeid="1807">确认环境之后，我们即可进入最后一步。</p>
<h4 data-nodeid="1808">第四步，Jupyter in VS Code</h4>
<p data-nodeid="1809">见证奇迹的时刻来临了，我们进入 VS Code 的插件 Tab（左侧边栏最下方的图标），输入 Jupyter 安装由微软官方出品的 Jupyter 插件（前几个有 Microsoft 字眼的）。</p>
<p data-nodeid="1810"><img src="https://s0.lgstatic.com/i/image6/M00/2D/6F/Cgp9HWBmj5aAKvGrAABUqOcg_gM988.png" alt="Drawing 8.png" data-nodeid="2057"></p>
<p data-nodeid="1811">安装完成之后，重启 VS Code（如果显示是禁用，那就是安装好了，直接操作后续即可）。按 【CTRL+P】 弹出命令面板，输入【&gt;Jupyter】，此时会列出所有 Jupyter 插件支持的操作，选择 【Jupyter: Create New Blank Jupyter Notebook】，如下图所示。</p>
<p data-nodeid="1812"><img src="https://s0.lgstatic.com/i/image6/M00/2D/6F/Cgp9HWBmj52AAWOfAAD8hk8ikao110.png" alt="Drawing 9.png" data-nodeid="2061"></p>
<p data-nodeid="1813">选择之后，VS Code 内部就出现了一个类似 Notebook 的编辑界面，和传统的网页版 Notebook不同，VS Code 中的Notebook 具备强大的代码提示和自动完成的功能。接下来，我们来学习一下它的主要操作。</p>
<p data-nodeid="1814">打开编辑界面，我们将 Notebook 可操作性的区域分为三个部分：主操作区、Cell 操作区、 边栏操作区。</p>
<p data-nodeid="1815"><img src="https://s0.lgstatic.com/i/image6/M01/2D/78/CioPOWBmkAmAGFRfAAIZXU8Ix7A173.png" alt="Drawing 11.png" data-nodeid="2066"></p>
<p data-nodeid="1816"><strong data-nodeid="2071">主操作区</strong>：主要用来控制整个 Notebook 的一些行为，从左到右的功能依次为：</p>
<ul data-nodeid="1817">
<li data-nodeid="1818">
<p data-nodeid="1819">运行全部 Cell；</p>
</li>
<li data-nodeid="1820">
<p data-nodeid="1821">运行上一个 Cell；</p>
</li>
<li data-nodeid="1822">
<p data-nodeid="1823">运行下一个 Cell；</p>
</li>
<li data-nodeid="1824">
<p data-nodeid="1825">重启 Kernel；</p>
</li>
<li data-nodeid="1826">
<p data-nodeid="1827">中断 Kernel；</p>
</li>
<li data-nodeid="1828">
<p data-nodeid="1829">插入 Cell；</p>
</li>
<li data-nodeid="1830">
<p data-nodeid="1831">清空结果；</p>
</li>
<li data-nodeid="1832">
<p data-nodeid="1833">展示活动的变量；</p>
</li>
<li data-nodeid="1834">
<p data-nodeid="1835">保存；</p>
</li>
<li data-nodeid="1836">
<p data-nodeid="1837">导出。</p>
</li>
</ul>
<blockquote data-nodeid="1838">
<p data-nodeid="1839">Kernel 代表在后台实际运行Python代码的服务。</p>
</blockquote>
<p data-nodeid="1840"><strong data-nodeid="2087">边栏操作区</strong>：不同位置的“+”号代表在不同位置插入 Cell。</p>
<p data-nodeid="1841"><strong data-nodeid="2092">Cell 操作区</strong>：主要用来控制当前 Cell 的行为，从左到右依次为：</p>
<ul data-nodeid="1842">
<li data-nodeid="1843">
<p data-nodeid="1844">运行 Cell（快捷键：【Shift + Enter】）；</p>
</li>
<li data-nodeid="1845">
<p data-nodeid="1846">逐行运行 Cell；</p>
</li>
<li data-nodeid="1847">
<p data-nodeid="1848">切换为文本模式（切换为文本模式后，点击"{}"图标可切换回代码模式）。</p>
</li>
</ul>
<p data-nodeid="1849">Cell是Notebook 中的核心概念，直译过来是“单元格”，但 Notebook 中的Cell 却不能用单元格简单概括，所以本文统一用Cell 描述，一个 Notebook 由多个 Cell 组成。</p>
<p data-nodeid="1850">Cell 一共有两种类型：</p>
<ul data-nodeid="1851">
<li data-nodeid="1852">
<p data-nodeid="1853"><strong data-nodeid="2106">代码Cell</strong>，主要用来编写 Python 代码，每个代码 Cell 都可以单独执行，并且执行结果会展示在 Cell的下方。</p>
</li>
<li data-nodeid="1854">
<p data-nodeid="1855"><strong data-nodeid="2111">文本 Cell</strong>，顾名思义，用来编写文本, 对于数据分析工作而言，除了代码本身，分析的思路、推导的逻辑同样非常重要，文本 Cell 就是用来承载这些内容。</p>
</li>
</ul>
<p data-nodeid="1856">这也是 Notebook 区别于 IPython 最大的地方，可以实现代码和文本的混排，来最大化的呈现数据分析的产出。</p>
<h3 data-nodeid="1857">Notebook 的基本操作</h3>
<p data-nodeid="1858">接下来，我们通过一个具体的任务，学习一下 Notebook 的基本操作。这些操作在后续的课程中会经常用到，我们先通过几个简单的小任务初步熟悉一下。</p>
<p data-nodeid="1859">任务目标如下。</p>
<ol data-nodeid="1860">
<li data-nodeid="1861">
<p data-nodeid="1862">创建一个 Notebook，保存为 my_practice.ipynb。</p>
</li>
<li data-nodeid="1863">
<p data-nodeid="1864">添加一个 Cell，通过代码打印“I am using Notebook”, 并运行。 在之后的课程中，我们每学完一个小阶段，都会通过新建一个 Cell 来编写代码测试我们学习的内容。</p>
</li>
<li data-nodeid="1865">
<p data-nodeid="1866">添加一个Cell，并转换成文本 Cell，输入文字“我的数据分析启程了！耶！”。在之后的课程中，我们希望把自己编写代码和分析的思路写下来的时候，往往就需要添加一个 Cell 并转换为文本模式这样来记录。这样最后我们的代码和分析文字都在同一个文件（Notebook）中，非常清晰。</p>
</li>
<li data-nodeid="1867">
<p data-nodeid="1868">添加一个 Cell，通过代码打印 1+1 的结果。</p>
</li>
</ol>
<p data-nodeid="1869">让我们来一步步实现上面的任务吧。</p>
<p data-nodeid="1870">第一步，按【CTRL + P】（Mac 对应【CMD + P】）， 调出 VS Code 的命令面板，输入【&gt; Jupyter】可以看到 Notebook 插件支持的命令，其中比较常用的几个如下。</p>
<blockquote data-nodeid="1871">
<p data-nodeid="1872"><strong data-nodeid="2144">1. Create New Black Jupyter Notebook：</strong> 创建新的空白 Notebook 工作区。<br>
<strong data-nodeid="2145">2. Export to PDF</strong>：将当前的Notebook 导出为 PDF，在后续写数据分析报告的时候会用到。<br>
<strong data-nodeid="2146">3. Import Jupyter Notebook</strong>：导入已有的Notebook。用来导入已有的 Notebook 文件，后续课程的所有 Notebook 我都会放到 Github 上共享，可以下载后导入运行。</p>
</blockquote>
<p data-nodeid="1873"><img src="https://s0.lgstatic.com/i/image6/M00/2D/78/CioPOWBmj9yAeI5CAADzIYou8DI414.png" alt="Drawing 12.png" data-nodeid="2149"></p>
<p data-nodeid="1874">今天我们首先选择第一个，创建一个新的Notebook，创建之后按 【CTRL + S】 保存，文件名输入：my_practice.ipynb。</p>
<p data-nodeid="1875">第二步，我们要新建 Cell，我们点击边栏操作区的 + 号即可新建 Cell， 然后我们输入以下代码：</p>
<p data-nodeid="1876"><img src="https://s0.lgstatic.com/i/image6/M01/2D/78/CioPOWBmkBaACcSMAACLIOFD0sg833.png" alt="Drawing 13.png" data-nodeid="2156"></p>
<pre class="lang-python" data-nodeid="1877"><code data-language="python">print(<span class="hljs-string">"I am using Notebook"</span>)
</code></pre>
<p data-nodeid="1878">点击 Cell 操作区中的“运行 Cell”，可以看到我们代码被执行，并打印出了上述字符串。效果如下图所示。</p>
<p data-nodeid="1879"><img src="https://s0.lgstatic.com/i/image6/M01/2D/78/CioPOWBmkCSAY9SxAABiiVr6B9o327.png" alt="Drawing 14.png" data-nodeid="2160"></p>
<p data-nodeid="1880">第三步，我们类似第二步首先新建一个 Cell，并点击 Cell 操作区中的 M 图标，切换为文本模式，并输入“我的数据分析启程了！耶！”。输入完毕后鼠标点击 Cell 之外的任意区域即可退出编辑模式，进入预览模式（双击 Cell 可重新进入编辑模式）。这样，我们的第三步就完成了。 如图所示。</p>
<p data-nodeid="1881"><img src="https://s0.lgstatic.com/i/image6/M01/2D/70/Cgp9HWBmkCuAd18YAACRFjQAhXU645.png" alt="Drawing 15.png" data-nodeid="2164"></p>
<p data-nodeid="1882">第四步，就很简单了，我们直接新建一个 Cell， 并输入以下代码：</p>
<pre class="lang-python" data-nodeid="1883"><code data-language="python">print(<span class="hljs-number">1</span>+<span class="hljs-number">1</span>)
</code></pre>
<p data-nodeid="1884">运行 Cell，可以看到打印了“2”，至此，我们的任务已经全部完成。整个过程如图所示。</p>
<p data-nodeid="1885"><img src="https://s0.lgstatic.com/i/image6/M01/2D/79/CioPOWBmkDKANTuZAAC7vrBVucI709.png" alt="Drawing 16.png" data-nodeid="2169"></p>
<h3 data-nodeid="1886">小结</h3>
<p data-nodeid="1887">至此，你已经在自己电脑上配置出一套面向数据分析的Python 开发环境，也知道如何新建 Notebook，以及在 Notebook中添加代码 Cell 来输入代码、文本 Cell 来输入文字。</p>
<p data-nodeid="1888">回顾下今天的内容，我主要强调了这几点：</p>
<ul data-nodeid="1889">
<li data-nodeid="1890">
<p data-nodeid="1891">对于需要编写 Python 代码进行数据分析的工作而言，一款具备强大的自动完成和错误提示的开发工具、掌握常用的快捷键会让你事半功倍；</p>
</li>
<li data-nodeid="1892">
<p data-nodeid="1893">使用 Anaconda + VS Code + Jupyter Notebook 插件，可以搭建一套具备代码提示和自动完成的、高效的、面向数据分析的开发环境；</p>
</li>
<li data-nodeid="1894">
<p data-nodeid="1895">你要学会 VS Code Notebook 的基本操作，这些基础我们后续都会用到。</p>
</li>
</ul>
<p data-nodeid="1896">搭建环境是用Python 做数据分析的第一步，为了让你学习更顺畅，<strong data-nodeid="2181">我们的视频观看形式附带了实操视频</strong>。如果你在搭建环境中还有什么问题，可以写在留言区，我会帮你扫清障碍，让你快速上手 Python。</p>
<p data-nodeid="1897">下一讲，我们将正式进入 Python 语言的世界，开始学习 Python 语言的基础：变量与数据类型。</p>
<blockquote data-nodeid="1898">
<p data-nodeid="1899"><strong data-nodeid="2194">彩蛋</strong><br>
本节课里会用到的快捷键：<br>
【CTRL + P】打开 VS Code 的命令面板；<br>
【Shift + Enter】运行当前 Cell；<br>
【Esc】退出当前 Cell 的编辑状态，退出编辑状态之后可以用方向键上下移动 Cell。</p>
</blockquote>

---

### 精选评论

##### **吹吹：
> 老师的工具链和主流教程好像不一样？

 ###### &nbsp;&nbsp;&nbsp; 讲师回复：
> &nbsp;&nbsp;&nbsp; 市面上的 Python 数据分析教程普遍带学员使用 Jupyter Notbook 或者 Spyder 集成开发环境，但这两者都或多或少缺乏必要的功能。

比如 Notebook 网页版不支持自动完成和错误提示，每次输入之后需要 Run 一次才能知道自己写的是否正确； Spyder 缺乏 Notebook 这样文档代码混排的机制，而数据分析往往需要文本和代码穿插展示，显然 Spyder 也是不符合要求的。
名词解释：
Jupyter Notebook：一款在网页上编写 Python 代码与文本的开发工具（下文简称 Notebook）
Spyder 集成开发环境：一款运行在 PC 上集开发、调试、发布为一身的综合性 Python 开发工具。

##### Eastjian：
> 我这里快捷键是【Ctrl+Shift+P】

##### **4562：
> 可以用这个环境开发web工程代码吗？web应用推荐哪个工具箱或者技术栈呢

 ###### &nbsp;&nbsp;&nbsp; 讲师回复：
> &nbsp;&nbsp;&nbsp; 可以的。但web就不需要jupyter 插件的。vs code最开始诞生就是为了写js的

##### **7554：
> Ctrl＋P创建新的jupyter notebook会默认将路径设置在C盘，这个怎么更改啊

 ###### &nbsp;&nbsp;&nbsp; 编辑回复：
> &nbsp;&nbsp;&nbsp; Ctrl+S

##### *击：
> 文本模式怎么编辑？

 ###### &nbsp;&nbsp;&nbsp; 讲师回复：
> &nbsp;&nbsp;&nbsp; 文本模式默认用 Markdown 语法来编写，双击可以进入编辑模式，编辑完毕后鼠标点击其他区域，可自动展示预览模式，即可预览编写的文本效果。
 
如果想要再进入编辑，则直接双击文本 Cell 即可。如上图中的文本在预览模式下展示如下图所示。

