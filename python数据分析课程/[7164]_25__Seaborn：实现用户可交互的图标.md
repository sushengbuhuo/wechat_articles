<p data-nodeid="4611">在之前的课程中，我们学习了 matplotlib 各种曲线的绘制方式，以及能够让图表变得更专业的刻度设置、图例设置以及注解的添加。但经过前面的学习，相信你也发现了一个问题，就是使用 matplotlib 来进行图表的绘制还是比较麻烦，步骤多，很烦琐。</p>
<p data-nodeid="4612">另一方面，matplotlib 问世时还没有 pandas，所以 matplotlib 和 pandas 的协同并不是很方便，在之前画图的例子中相信你也感受到了，更多都需要用 numpy 的 ndarray 作为中转。</p>
<p data-nodeid="4613">现阶段随着数据分析的蓬勃发展，人们基于 matplotlib 开发了新一代更好用的绘图工具包：seaborn。 今天我们就来学习如何使用 seaborn ，来用更简洁的代码绘制更漂亮的曲线。</p>
<h3 data-nodeid="4614">初识 seaborn</h3>
<p data-nodeid="4615">seaborn 并不是一套全新的工具包，而是基于 matplotlib 进行了扩展，在使用的时候仍然是和 matplotlib 的函数们配合使用的。</p>
<p data-nodeid="4616">使用 seaborn 的主要方式有两种：</p>
<ul data-nodeid="4617">
<li data-nodeid="4618">
<p data-nodeid="4619">只是使用 seaborn 的样式，但仍然使用 matplotlib 的函数；</p>
</li>
<li data-nodeid="4620">
<p data-nodeid="4621">seaborn 的全新函数。</p>
</li>
</ul>
<p data-nodeid="4622">接下来我们会分别进行介绍。</p>
<p data-nodeid="4623">第一步，我们仍然是安装 seaborn。</p>
<h4 data-nodeid="4624">安装 seaborn</h4>
<p data-nodeid="4625">打开开始菜单 → Anaconda3 → Anaconda Prompt， 输入 conda install seaborn 并回车，如下图所示。</p>
<p data-nodeid="7351" class=""><img src="https://s0.lgstatic.com/i/image6/M00/49/2B/Cgp9HWDZpBmASaIcAAKKXr4nmAU852.png" alt="Drawing 0.png" data-nodeid="7354"></p>

<p data-nodeid="4627">输入 y 回车，完成安装。</p>
<p data-nodeid="4628">另外，plotly 是用来绘制交互式图表的工具包。我们在 seaborn 的章节也会用到 plotly 的数据集，所以我们一并安装 plotly。方法同上，安装命令为： conda install plotly。</p>
<h4 data-nodeid="4629">比较 matplotlib 和 seaborn 的样式</h4>
<p data-nodeid="4630">首先，我们用一个简单的例子来看一下 seaborn 和 matplotlib 样式上的区别。</p>
<p data-nodeid="4631">准备实验环境，在课程目录新建 chapter25 目录，并在 VScode 中打开该目录，并新建 Notebook，保存为 chapter25.ipynb。</p>
<p data-nodeid="4632">之后导入需要使用的工具包：</p>
<pre class="lang-python" data-nodeid="4633"><code data-language="python"><span class="hljs-keyword">import</span>&nbsp;pandas&nbsp;<span class="hljs-keyword">as</span>&nbsp;pd
<span class="hljs-keyword">import</span>&nbsp;seaborn&nbsp;<span class="hljs-keyword">as</span>&nbsp;sns&nbsp;
<span class="hljs-keyword">import</span>&nbsp;matplotlib.pyplot&nbsp;<span class="hljs-keyword">as</span>&nbsp;plt
<span class="hljs-keyword">import</span>&nbsp;numpy&nbsp;<span class="hljs-keyword">as</span>&nbsp;np
</code></pre>
<p data-nodeid="4634">我们以之前画过的直方图为例，首先是准备一个正态分布的数据源：</p>
<pre class="lang-python" data-nodeid="4635"><code data-language="python">np.random.seed(<span class="hljs-number">100</span>)
hints&nbsp;=&nbsp;np.random.normal(<span class="hljs-number">5</span>,&nbsp;<span class="hljs-number">10</span>,&nbsp;<span class="hljs-number">1000</span>)
</code></pre>
<p data-nodeid="4636">然后直接使用默认的样式来画出直方图：</p>
<pre class="lang-python" data-nodeid="4637"><code data-language="python">figure1&nbsp;=&nbsp;plt.figure(figsize&nbsp;=&nbsp;(<span class="hljs-number">10</span>,&nbsp;<span class="hljs-number">5</span>))
figure1.add_subplot(<span class="hljs-number">1</span>,<span class="hljs-number">1</span>,<span class="hljs-number">1</span>)
plt.hist(hints,&nbsp;bins=<span class="hljs-number">50</span>)
plt.show()
</code></pre>
<p data-nodeid="4638">执行之后，图形如下所示。</p>
<p data-nodeid="8451" class=""><img src="https://s0.lgstatic.com/i/image6/M00/49/34/CioPOWDZpCOAYQEQAACYhMCMENs962.png" alt="Drawing 2.png" data-nodeid="8454"></p>


<p data-nodeid="4641">这个图之前我们就已经画出来过，可以说 matplotlib 如果不额外进行样式指定的话，图像的可读性还是比较差的。</p>
<p data-nodeid="4642">现在，我们来试一下用 seaborn 的样式改造这个直方图。我们只需要设置激活 seaborn 的样式，然后用 matplotlib 的函数，这样直方图就自动被应用上 seaborn 样式了。</p>
<p data-nodeid="4643">激活 seaborn 样式的代码如下：</p>
<pre class="lang-python" data-nodeid="4644"><code data-language="python">sns.set()
</code></pre>
<p data-nodeid="4645">是的，你没看错，就是这么简单。执行完上述 Cell 之后，重新执行一遍刚才我们画直方图的代码，画出来的图形如下所示。可以看到，在我们什么都不做的时候， seaborn 画的图明显更好看一些。</p>
<p data-nodeid="9551" class=""><img src="https://s0.lgstatic.com/i/image6/M00/49/2B/Cgp9HWDZpCyAANGpAADWCrSPl2o531.png" alt="Drawing 4.png" data-nodeid="9554"></p>


<h3 data-nodeid="4648">seaborn 常见曲线的绘制</h3>
<p data-nodeid="4649">接下来，我们来学习 seaborn 常见的几种曲线的绘制方式。为了方便演示，我们选择行业通用的 iris 数据集作为例子。</p>
<h4 data-nodeid="4650">数据集准备</h4>
<p data-nodeid="4651"><a href="https://baike.baidu.com/item/IRIS/4061453?fr=aladdin" data-nodeid="4920">iris 数据集</a>是常见的用来做数据分析以及分类分析的数据集。有 150 个数据样本，每个样本包含五个字段，如下所示。iris 数据集简单、易于分析，且容易建立出根据花瓣和花萼的长宽来对花的类型进行分类的模型，所以被广泛应用于数据分析的各类教学中。所以掌握 iris 数据集对大家的数据分析之路也是非常有帮助的。</p>
<p data-nodeid="10651" class=""><img src="https://s0.lgstatic.com/i/image6/M00/49/34/CioPOWDZpDSAGhL0AABp4Ah9y8o499.png" alt="Drawing 5.png" data-nodeid="10654"></p>


<p data-nodeid="4678">plotly 数据包中有现成的 iris 数据，所以我们并不需要从 csv 中读取。代码如下：</p>
<pre class="lang-python" data-nodeid="4679"><code data-language="python"><span class="hljs-keyword">import</span>&nbsp;plotly.express&nbsp;<span class="hljs-keyword">as</span>&nbsp;px
df_iris&nbsp;=&nbsp;px.data.iris()
df_iris
</code></pre>
<p data-nodeid="4680">输出如下：</p>
<p data-nodeid="11661" class=""><img src="https://s0.lgstatic.com/i/image6/M00/49/34/CioPOWDZpDqAPcb1AACx-nD0yKI551.png" alt="Drawing 6.png" data-nodeid="11664"></p>

<p data-nodeid="4682">可以看到，DataFrame 的内容和我们的描述基本一致，只是多了一个 species_id。这个其实就是分类的 id，可以不用理会。</p>
<h4 data-nodeid="4683">折线图</h4>
<p data-nodeid="4684">seaborn 区别于原生 matlotlib 最明显的一点，就是 seaborn 和 pandas 进行了<strong data-nodeid="4957">深度的整合</strong>，使得画图的代码大幅减少。比如我们希望画出花瓣宽度的折线图，只需要一行代码：</p>
<pre class="lang-python" data-nodeid="4685"><code data-language="python">df_iris.petal_width.plot()
</code></pre>
<p data-nodeid="4686">输出如下：</p>
<p data-nodeid="12675" class=""><img src="https://s0.lgstatic.com/i/image6/M00/49/2C/Cgp9HWDZpEKAeqMnAAL2QVsYen4664.png" alt="Drawing 8.png" data-nodeid="12678"></p>


<p data-nodeid="4689">我们甚至没有调用任何的绘图代码，seaborn 就扩展了 DataFrame 和 Series 对象，给它们加上了 plot 方法，这样我们直接调用我们想绘制的数据源对象的 plot 函数就可以完成绘图。</p>
<p data-nodeid="4690">一般调用 DataFrame 或者 Series 的 plot  方法时，横轴默认使用 DataFrame 的 index 作为横轴的数据源。我们甚至可以直接调用 DataFrame 的 plot 方法，来一次性地将所有列绘制在图表上。</p>
<p data-nodeid="4691">代码如下：</p>
<pre class="lang-python" data-nodeid="4692"><code data-language="python">df_iris.plot()
</code></pre>
<p data-nodeid="13689" class="">输出如下：<br>
<img src="https://s0.lgstatic.com/i/image6/M00/49/34/CioPOWDZpaWAICZZAAaBo_SeyhQ346.png" alt="Drawing 10.png" data-nodeid="13694"></p>


<p data-nodeid="4695">可以看到，DataFrame 中所有字段的曲线都被画在了画布上，并且自动都有图例来显示不同曲线对应的哪个字段。seaborn 的好处就是，往往不需要多少特别的设置，就能获得不错的结果。</p>
<h4 data-nodeid="4696">直方图</h4>
<p data-nodeid="4697">接下来我们来学习直方图，比如我们希望统计记录中花瓣宽度的分布图。</p>
<p data-nodeid="4698">同样只需要一行代码就可以，如下所示：</p>
<pre class="lang-python" data-nodeid="4699"><code data-language="python">df_iris.petal_width.plot.hist()
</code></pre>
<p data-nodeid="14705" class="">输出之后显示：<br>
<img src="https://s0.lgstatic.com/i/image6/M00/49/34/CioPOWDZpbOAcG54AADq8MqFKQE802.png" alt="Drawing 12.png" data-nodeid="14710"></p>


<p data-nodeid="4702">seaborn 除了给 DataFrame 和 Series 添加了 plot 方法，还添加了 plot 对象，如我们上述代码就是调用了 plot 对象的 hist 方法，来实现直方图的绘制。</p>
<h4 data-nodeid="4703">核密度图</h4>
<p data-nodeid="4704">核密度图是数据分析中非常常见的一种分析手段，其功能类似于直方图，也是用于观察数据分布的工具之一。核密度图展示的是概率分布，直方图展示的是频率，有时候我们的分析的数据往往是有限的，有的数据区域没有直方图画出来的时候，是不是就代表一定不存在呢？肯定不是的，只是可能出现概率比较低，所以没有被收录到数据集而已。核密度图就能够比较好地表示这类信息。</p>
<p data-nodeid="4705">核密度的估计是直方图的一种自然扩展，可以认为是平滑版的直方图。核密度曲线是一种概率密度曲线，曲线下的面积是 1，y 轴上的单位通常是小于 1 的概率分布值。</p>
<p data-nodeid="4706">seaborn 提供 kdeplot 方法来绘制核密度图。我们还是以之前的花瓣宽度为例，花瓣宽度的核密度图，代码如下：</p>
<pre class="lang-python" data-nodeid="4707"><code data-language="python">sns.kdeplot(df_iris.petal_width,&nbsp;shade=<span class="hljs-literal">True</span>)
</code></pre>
<p data-nodeid="15721" class="">输出如下：<br>
<img src="https://s0.lgstatic.com/i/image6/M01/49/2C/Cgp9HWDZpb6AX8ttAAHRSgTCEIs484.png" alt="Drawing 14.png" data-nodeid="15726"><br>
可以看到，从形状上来看，概率密度图和直方图是相对接近的。</p>



<h4 data-nodeid="4711">直方核密度图</h4>
<p data-nodeid="4712">从上面的例子中，相信你也已经发现，直方图和核密度图往往是一起分析的。seaborn 提供了一个 histplot 方法，可以在绘制直方图时同时也画出对应的概率密度曲线。</p>
<p data-nodeid="4713">代码如下：</p>
<pre class="lang-python" data-nodeid="4714"><code data-language="python">sns.histplot(df_iris.petal_width,&nbsp;kde=<span class="hljs-literal">True</span>)
</code></pre>
<p data-nodeid="16739" class="">输出<br>
<img src="https://s0.lgstatic.com/i/image6/M01/49/2C/Cgp9HWDZpciAWHRrAAFsriUgB0w271.png" alt="Drawing 16.png" data-nodeid="16744"></p>


<h4 data-nodeid="4717">二维核密度图</h4>
<p data-nodeid="4718">之前我们绘制的都是单一变量的核密度图，seaborn 的 kdeplot 函数还支持绘制二维的核密度图，就是在一张图上体现两个变量的概率分布。二维的核密度图可以帮助我们从概率分布的角度来分析两个变量的相关性。</p>
<p data-nodeid="4719">这时候只需要分别指定 data 参数， x 参数和 y 参数即可。我们来看 petal_width 和 sepal_width 两个列的概率分布。代码如下：</p>
<pre class="lang-python" data-nodeid="4720"><code data-language="python">sns.kdeplot(data=df_iris,&nbsp;x=<span class="hljs-string">"petal_width"</span>,&nbsp;y=<span class="hljs-string">"sepal_width"</span>)
</code></pre>
<p data-nodeid="17755" class="">输出如下：<br>
<img src="https://s0.lgstatic.com/i/image6/M00/49/34/CioPOWDZpdiAPT9GAAR8tqT6Zb0507.png" alt="Drawing 18.png" data-nodeid="17760"></p>


<p data-nodeid="4723">直接这样看可能并不明显，我们可以加上 shade 参数，设置为 True。</p>
<p data-nodeid="4724">添加 shade 参数后的效果如下：</p>
<p data-nodeid="18771" class=""><img src="https://s0.lgstatic.com/i/image6/M00/49/34/CioPOWDZpeSATEq1AAG--hf9ihE323.png" alt="Drawing 20.png" data-nodeid="18774"></p>


<p data-nodeid="4727">这样就能比较明显地看到颜色越深的地方，概率分布越密集。</p>
<h4 data-nodeid="4728">pairplot</h4>
<p data-nodeid="4729">除了以上常见的图形，seaborn 还提供了一种非常方便的分析相关性图表：pairplot。</p>
<p data-nodeid="4730">pairplot 是一种特殊的图表，它能够显示 DataFrame 中字段两两之间的关系。非常适合在我们还不够了解数据集的时候，直接把所有字段的关系以图表的形式绘制出来，做第一步的探索。比如我们拿到一个房价数据集，有单价、面积、地段等，单价和面积可能有关系，面积和地段可能也有关系，与其我们一个个去看特征的相关性，我们可以直接把整个表的 pairplot 画出来，就能够一目了然地看到它们之间的关系。</p>
<p data-nodeid="4731">以 iris 数据集为例，我们希望查看特征两两之间的关系，因为要绘制图表，所以只有数字类型的特征会被用来画图，species_id 这一列可能会导致问题，因为本质这是一个类别的标识（只有三个取值）。所以第一步，我们首先将这一列删除。</p>
<pre class="lang-python" data-nodeid="4732"><code data-language="python">df_iris&nbsp;=&nbsp;df_iris.drop(columns=[<span class="hljs-string">"species_id"</span>])
</code></pre>
<p data-nodeid="4733">第二步，绘制 iris 数据集的 pairplot。</p>
<pre class="lang-python" data-nodeid="4734"><code data-language="python">sns.pairplot(df_iris,&nbsp;hue=<span class="hljs-string">"species"</span>)
</code></pre>
<p data-nodeid="4735">输出如下：</p>
<p data-nodeid="19785" class=""><img src="https://s0.lgstatic.com/i/image6/M01/49/2C/Cgp9HWDZpfGAVBLOAAMOULq3oXE658.png" alt="Drawing 22.png" data-nodeid="19788"></p>


<p data-nodeid="4738">可以看到，输出了非常丰富的一个图标，横轴和纵轴都是各个特征。每个子图都代表某两个特征的散点图。比如四三行第四列的图，petal_length 和 petal_width，从图上就能很明显看出这两个特征是正相关的。在对角线上代表同一个特征的比较，比如第一行第一列，第二行第二列，都是同一个特征的相关性，但同一个特征其实不存在相关性一说，所以就以直方图来表示了。</p>
<p data-nodeid="4739">当然，我们还可以更进一步。因为 species 字段是字符串内容，没有画在里面，但我们可以把图像中不同的 species 数据用不同的颜色标出来，也能够看出很多额外的信息。</p>
<p data-nodeid="4740">在 pairplot 中，如果我们希望图像根据某个字段进行分类，只需要指定 hue 参数即可。代码如下：</p>
<pre class="lang-python" data-nodeid="4741"><code data-language="python">sns.pairplot(df_iris,&nbsp;hue=<span class="hljs-string">"species"</span>)
</code></pre>
<p data-nodeid="20799" class="">输出如下：<br>
<img src="https://s0.lgstatic.com/i/image6/M00/49/34/CioPOWDZpfyAP3T4AAOl2cRiBdM594.png" alt="Drawing 24.png" data-nodeid="20804"></p>


<p data-nodeid="4744">这次的 pairplot 相比纯特征比较，表示出了更多的特征，比如 setosa 类型（蓝色）数据就非常容易区别，比如从第三行第一列的图就能发现，我们可以简单通过 petal_length 就能够把setosa 类型的花分类出来。</p>
<p data-nodeid="4745">综上所述，对于数据量不是很大的数据集来说，我们直接通过 pairplot， 一次性地把所有相关的特征数据绘制出来，是非常有效的分析手段。</p>
<h3 data-nodeid="4746">绘制可交互的图表</h3>
<p data-nodeid="4747">通过前面内容的学习，相信你也感受到了 seaborn 的强大本领，它能够用非常少的代码来绘制出更好看、丰富的图表。</p>
<p data-nodeid="4748">接下来我们更近一步，介绍一种更先进的图表绘制技术：可交互的图表。</p>
<p data-nodeid="4749">在之前工具安装的环节，我们就提到过绘制可交互图表的工具叫 plotly，之前我们已经安装完毕了。plotly 支持的可交互图表的类型非常多，教程无法一一列举。</p>
<p data-nodeid="4750">接下来，我就来举两个比较有代表性的例子，来演示可交互图表的基础以及所支持的交互方式。</p>
<p data-nodeid="4751">首先，我们先导入 plotly 工具包：</p>
<pre class="lang-python" data-nodeid="4752"><code data-language="python"><span class="hljs-keyword">import</span>&nbsp;plotly.express&nbsp;<span class="hljs-keyword">as</span>&nbsp;px
<span class="hljs-keyword">from</span>&nbsp;plotly.offline&nbsp;<span class="hljs-keyword">import</span>&nbsp;init_notebook_mode,&nbsp;iplot,&nbsp;plot&nbsp;
<span class="hljs-keyword">import</span>&nbsp;plotly.graph_objs&nbsp;<span class="hljs-keyword">as</span>&nbsp;go&nbsp;
</code></pre>
<h4 data-nodeid="4753">绘制可交互图表</h4>
<p data-nodeid="4754">可交互散点图的绘制非常简单，只需要调用 px 模块的 scatter 函数，构造出图表对象。然后调用图表对象的 show 方法即可。</p>
<p data-nodeid="4755">以绘制 iris 数据集中 sepal_width 和 sepal_length 的特征为例：</p>
<pre class="lang-python" data-nodeid="4756"><code data-language="python"><span class="hljs-comment"># 指定 x/y 轴的数据源，以及基于哪一列做颜色区分，这里选择用种类一类来做颜色的区分</span>
fig&nbsp;=&nbsp;px.scatter(df_iris,&nbsp;x=<span class="hljs-string">"sepal_width"</span>,&nbsp;y=<span class="hljs-string">"sepal_length"</span>,&nbsp;color=<span class="hljs-string">"species"</span>)
fig.show()
</code></pre>
<p data-nodeid="21815" class="">输出如下：<br>
<img src="https://s0.lgstatic.com/i/image6/M01/49/2C/Cgp9HWDZpjGAAzuxAAFKPFDZh5k829.png" alt="Drawing 26.png" data-nodeid="21820"></p>


<p data-nodeid="4759">整体绘图方式和 seaborn 差别并不大。</p>
<h4 data-nodeid="4760">plotly 基本交互要素</h4>
<p data-nodeid="4761">绝大多数 plotly 图像的交互形式都是相对确定的，一般都分为三个可操作区：</p>
<p data-nodeid="22831" class=""><img src="https://s0.lgstatic.com/i/image6/M01/49/2C/Cgp9HWDZpjmAfWNVAAGdmPDnl3w189.png" alt="Drawing 28.png" data-nodeid="22834"></p>


<p data-nodeid="4764">（1）操作区 1：图表区域</p>
<p data-nodeid="4765">操作区 1 就是图表的曲线绘制的区域，这个操作区里 plotly 支撑两个主要的操作方式。首先是鼠标悬停在数据点上方时，可以显示该数据点的相关信息，比如对应 x 轴和 y 轴的点，以及对应的 species。</p>
<p data-nodeid="23845" class=""><img src="https://s0.lgstatic.com/i/image6/M01/49/2C/Cgp9HWDZpkKAdDz3AAFx_APQix8378.png" alt="Drawing 30.png" data-nodeid="23848"></p>


<p data-nodeid="4768">第二个交互方式是可以鼠标单击拖拽，可以将局部区域放大。</p>
<p data-nodeid="4769">拖拽期间的效果如下所示</p>
<p data-nodeid="24859" class=""><img src="https://s0.lgstatic.com/i/image6/M00/49/35/CioPOWDZpkmADokmAAFqYOtuf3c723.png" alt="Drawing 32.png" data-nodeid="24862"></p>


<p data-nodeid="4772">拖拽结束后，拖拽选择的区域被放大，效果如下所示：</p>
<p data-nodeid="25873" class=""><img src="https://s0.lgstatic.com/i/image6/M00/49/35/CioPOWDZplGAdW4QAAD-KlKCP6c722.png" alt="Drawing 34.png" data-nodeid="25876"></p>


<p data-nodeid="4775">可以看到，图像已经变成我们刚才鼠标拖动的选择框区域。</p>
<p data-nodeid="4776">（2）操作区 2：图例区域</p>
<p data-nodeid="4777">操作区 2 其实就是我们之前的讲过的图例区域，对于 plotly 绘制的曲线，图例都是可以点击的。点击图例可以控制显示或者隐藏某个分类，比如我们点击 setosa 这个图例，可以看到 setosa 类别的紫色点隐藏了，图像里只剩下另外两个类别的数据点，如下所示。</p>
<p data-nodeid="26887" class=""><img src="https://s0.lgstatic.com/i/image6/M00/49/35/CioPOWDZplqAdDxFAAEoknXLdT0218.png" alt="Drawing 36.png" data-nodeid="26890"></p>


<p data-nodeid="4780">对于隐藏的图例，再次点击可以重新显示。通过这个功能，我们可以把暂时不感兴趣的数据点隐藏，帮助我们更聚焦在当前看的数据类别，非常好用。</p>
<p data-nodeid="4781">（3）操作区 3：工具栏区</p>
<p data-nodeid="4782">操作区 3 是顶部工具栏的区域，从左到右的功能依次为：</p>
<ul data-nodeid="29461">
<li data-nodeid="29462">
<p data-nodeid="29463">保存 JPG</p>
</li>
<li data-nodeid="29464">
<p data-nodeid="29465">放大缩小</p>
</li>
<li data-nodeid="29466">
<p data-nodeid="29467">移动</p>
</li>
<li data-nodeid="29468">
<p data-nodeid="29469">矩形选择（就是之前我们的鼠标拖动矩形框）</p>
</li>
<li data-nodeid="29470">
<p data-nodeid="29471">套索选择（可以支持选不规则的曲线区域）</p>
</li>
<li data-nodeid="29472">
<p data-nodeid="29473">放大</p>
</li>
<li data-nodeid="29474">
<p data-nodeid="29475">缩小</p>
</li>
<li data-nodeid="29476">
<p data-nodeid="29477">自动放缩</p>
</li>
<li data-nodeid="29478">
<p data-nodeid="29479">重置曲线</p>
</li>
<li data-nodeid="29480">
<p data-nodeid="29481">显示辅助线</p>
</li>
<li data-nodeid="29482">
<p data-nodeid="29483">悬浮框显示一个点</p>
</li>
<li data-nodeid="29484">
<p data-nodeid="29485">悬浮框显示两个点</p>
</li>
</ul>
<p data-nodeid="30524"><img src="https://s0.lgstatic.com/i/image6/M01/49/2C/Cgp9HWDZpn2AQrnlAAHaGqhIutg581.png" alt="Drawing 38.png" data-nodeid="30527"></p>







<p data-nodeid="4810">这里我选择性地讲几个比较常用的操作。</p>
<p data-nodeid="4811">第一个是辅助线，点击、打开之后。当我们鼠标移动到具体的数据点上时，会有线条给我们标注出该数据点在 x 轴和 y 轴的位置，如下所示。</p>
<p data-nodeid="31538" class=""><img src="https://s0.lgstatic.com/i/image6/M00/49/35/CioPOWDZpnKAEueQAAE1sYifY-Q002.png" alt="Drawing 40.png" data-nodeid="31541"></p>


<p data-nodeid="4814">另外一个较为常用的功能就是悬浮显示两个点，简单来说就是悬浮窗口中会显示鼠标附近的两个点信息，作为一个比较，如下图所示。</p>
<p data-nodeid="32552" class=""><img src="https://s0.lgstatic.com/i/image6/M00/49/35/CioPOWDZpoeALPh3AAF7zecT9lg962.png" alt="Drawing 42.png" data-nodeid="32555"></p>


<p data-nodeid="4817">这个功能在我们分析数据点和附近区域关系时非常方便。</p>
<h4 data-nodeid="4818">常见的 plotly 图形的绘制</h4>
<p data-nodeid="4819">plotly 图形的绘制和 seaborn 大同小异，无非就是指定数据源 x 和 y 即可，简单举几个例子。</p>
<p data-nodeid="4820">（1）气泡图</p>
<p data-nodeid="4821">气泡图本质上就是点的大小不一的散点图，简单来说就是，我们可以用 scatter 函数的 size 参数，来指定数据点的大小。这样就能在散点图的基础上反映出数据点的一些其他维度信息。</p>
<p data-nodeid="4822">比如拿刚才的散点图为例：</p>
<p data-nodeid="33566" class=""><img src="https://s0.lgstatic.com/i/image6/M01/49/2C/Cgp9HWDZppGAR5gvAAFPeNqKQFs918.png" alt="Drawing 44.png" data-nodeid="33569"></p>


<p data-nodeid="4825">我们绘制了 sepal_width 和 sepal_length 的关系图，这个时候我们如果想看额外的特征，比如 petal_width 和它们的关系，我们可以将其指定为 size 的参数，代码如下：</p>
<pre class="lang-python" data-nodeid="4826"><code data-language="python">fig&nbsp;=&nbsp;px.scatter(df_iris,&nbsp;x=<span class="hljs-string">"sepal_width"</span>,&nbsp;y=<span class="hljs-string">"sepal_length"</span>,&nbsp;color=<span class="hljs-string">"species"</span>,&nbsp;size=<span class="hljs-string">"petal_width"</span>)
fig.show()
</code></pre>
<p data-nodeid="34580" class="">输出如下：<br>
<img src="https://s0.lgstatic.com/i/image6/M01/49/2C/Cgp9HWDZpp-ANhwpAAJ0U28IkvI975.png" alt="Drawing 46.png" data-nodeid="34585"></p>


<p data-nodeid="4829">这样上图里的数据点就变成了大小不一的气泡，大小则是由 petal_width 来决定。从图里不难看出，似乎 virginica 类型的鸢尾花的 petal_width 比较大。</p>
<p data-nodeid="4830">（2）折线图</p>
<p data-nodeid="4831">plotly 的折线图用的是 line 函数，用法如下：</p>
<pre class="lang-python" data-nodeid="4832"><code data-language="python">fig1&nbsp;=&nbsp;px.line(df_iris[[<span class="hljs-string">"petal_width"</span>,<span class="hljs-string">"petal_length"</span>]])
fig1.show()
</code></pre>
<p data-nodeid="35596" class="">输出如下：<br>
<img src="https://s0.lgstatic.com/i/image6/M01/49/2C/Cgp9HWDZpqiALdVjAAHyNLq--WA537.png" alt="Drawing 48.png" data-nodeid="35601"></p>


<p data-nodeid="4835">（3）直方图</p>
<p data-nodeid="4836">直方图则使用 histogram 函数，用法如下：</p>
<pre class="lang-python" data-nodeid="4837"><code data-language="python">fig2&nbsp;=&nbsp;px.histogram(df_iris[[<span class="hljs-string">"sepal_length"</span>]])
fig2.show()
</code></pre>
<p data-nodeid="36612" class="">输出如下：<br>
<img src="https://s0.lgstatic.com/i/image6/M01/49/2C/Cgp9HWDZprCAcSPIAACR9SLTj0E652.png" alt="Drawing 50.png" data-nodeid="36617"></p>


<h3 data-nodeid="4840">小结</h3>
<p data-nodeid="4841">至此，我们关于 seaborn 和 plotly 的一些基本知识就介绍完毕了。算下来我们一共学习了三套绘图的技术：matplotlib，seaborn 和 plotly。</p>
<p data-nodeid="4842">那我们在实际项目中该如何选择呢？ 一般情况下，可以遵循以下的标准：</p>
<ul data-nodeid="4843">
<li data-nodeid="4844">
<p data-nodeid="4845">简单绘制图表即可——使用 seaborn；</p>
</li>
<li data-nodeid="4846">
<p data-nodeid="4847">需要比较多的定制、子图的排布等——使用 seaborn 的样式 + matplotlib 绘图；</p>
</li>
<li data-nodeid="4848">
<p data-nodeid="4849">绘制的图表信息量较大，希望用户可以进行交互——使用 plotly。</p>
</li>
</ul>
<p data-nodeid="4850">我们也简单回顾一下今天所学习的内容。</p>
<p data-nodeid="4851">首先是 seaborn，我们可以：</p>
<ul data-nodeid="4852">
<li data-nodeid="4853">
<p data-nodeid="4854">使用 sns.set() 激活seaborn 的样式；</p>
</li>
<li data-nodeid="4855">
<p data-nodeid="4856">使用 DataFrame / Series 的plot 方法绘制折线图，plot.hist 方法绘制直方图；</p>
</li>
<li data-nodeid="4857">
<p data-nodeid="4858">使用 sns.kdeplot 绘制核密度图；</p>
</li>
<li data-nodeid="4859">
<p data-nodeid="4860">使用 sns.histplot 配合 kde 参数，来将直方图和核密度图同事绘制；</p>
</li>
<li data-nodeid="4861">
<p data-nodeid="4862">使用 pairplot 一次性绘制所有特征两两关系大图。</p>
</li>
</ul>
<p data-nodeid="4863">之后，我们学习了 plotly，主要包括：</p>
<ul data-nodeid="4864">
<li data-nodeid="4865">
<p data-nodeid="4866">使用 px.data.iris() ，直接加载 iris 数据集；</p>
</li>
<li data-nodeid="4867">
<p data-nodeid="4868">使用 px.scatter ，绘制散点图，增加 size 属性则可以绘制气泡图；</p>
</li>
<li data-nodeid="4869">
<p data-nodeid="4870">plotly 图表的基本操作；</p>
</li>
<li data-nodeid="4871">
<p data-nodeid="4872">使用 px.line 绘制折线图；</p>
</li>
<li data-nodeid="4873">
<p data-nodeid="4874">使用 px.histogram 绘制直方图。</p>
</li>
</ul>
<p data-nodeid="4875">至此，我们数据可视化的知识部分就基本讲完了，下一讲我们将会以一个实战案例来演示数据可视化是如何帮助我们做数据分析的。</p>
<p data-nodeid="4876">课后作业：</p>
<p data-nodeid="4877">针对 iris 数据集，绘制所有山鸢尾四个特征的直方核密度图。</p>
<hr data-nodeid="4878">
<p data-nodeid="4879">答案如下：</p>
<pre class="lang-python" data-nodeid="4880"><code data-language="python">sns.histplot(df_iris[df_iris[<span class="hljs-string">"species"</span>]==<span class="hljs-string">"setosa"</span>],&nbsp;kde=<span class="hljs-literal">True</span>)
</code></pre>
<p data-nodeid="37628" class="te-preview-highlight">输出如下：<br>
<img src="https://s0.lgstatic.com/i/image6/M01/49/35/CioPOWDZprmAahjoAAJqp4FZnB8891.png" alt="Drawing 52.png" data-nodeid="37633"></p>

---

### 精选评论


