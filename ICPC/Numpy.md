
<p>今回も例としてNumpyのコードを書いてますが、それらは、以下のようにNumpyをインポートしていることを前提にしています。</p>
<blockquote>
<p>import numpy as np</p>
</blockquote>
<p> さて。</p>
<p> </p>
<h4>Numpy配列内の型（dtype指定）</h4>
<p> </p>
<p>Numpyは配列内はすべて同じ型にそろえられます。</p>
<p>型を指定して生成できますし、データを与えて生成すると適切なものにしてくれるみたいですが、いちおうデフォルトは<a class="keyword" href="http://d.hatena.ne.jp/keyword/python">python</a>のfloatと互換性のある「float_」という型になります。</p>
<table>
<tbody>
<tr>
<th>dtype</th>
<th>互換性</th>
<th>コメント</th>
</tr>
<tr>
<td>float_</td>
<td><a class="keyword" href="http://d.hatena.ne.jp/keyword/Python">Python</a>の「float」</td>
<td>Numpyのデフォルト</td>
</tr>
<tr>
<td>uint</td>
<td><a class="keyword" href="http://d.hatena.ne.jp/keyword/Python">Python</a>の「int」</td>
<td>符号なし</td>
</tr>
<tr>
<td>int_</td>
<td><a class="keyword" href="http://d.hatena.ne.jp/keyword/Python">Python</a>の「int」</td>
<td>符号あり</td>
</tr>
<tr>
<td>bool_</td>
<td><a class="keyword" href="http://d.hatena.ne.jp/keyword/Python">Python</a>の「bool」</td>
<td> </td>
</tr>
<tr>
<td>int8</td>
<td>8ビット整数</td>
<td>符号あり</td>
</tr>
<tr>
<td>int16</td>
<td>16ビット整数</td>
<td>符号あり</td>
</tr>
<tr>
<td>int32</td>
<td>32ビット整数</td>
<td>符号あり</td>
</tr>
<tr>
<td>int64</td>
<td>64ビット整数</td>
<td>符号あり</td>
</tr>
<tr>
<td>uint8</td>
<td>8ビット整数</td>
<td>符号なし</td>
</tr>
<tr>
<td>uint16</td>
<td>16ビット整数</td>
<td>符号なし</td>
</tr>
<tr>
<td>uint32</td>
<td>32ビット整数</td>
<td>符号なし</td>
</tr>
<tr>
<td>uint64</td>
<td>64ビット整数</td>
<td>符号なし</td>
</tr>
<tr>
<td>float16</td>
<td>16ビット<a class="keyword" href="http://d.hatena.ne.jp/keyword/%C9%E2%C6%B0%BE%AE%BF%F4%C5%C0%BF%F4">浮動小数点数</a></td>
<td> </td>
</tr>
<tr>
<td>float32</td>
<td>32ビット<a class="keyword" href="http://d.hatena.ne.jp/keyword/%C9%E2%C6%B0%BE%AE%BF%F4%C5%C0%BF%F4">浮動小数点数</a></td>
<td> </td>
</tr>
<tr>
<td>float64</td>
<td>64ビット<a class="keyword" href="http://d.hatena.ne.jp/keyword/%C9%E2%C6%B0%BE%AE%BF%F4%C5%C0%BF%F4">浮動小数点数</a></td>
<td> </td>
</tr>
</tbody>
</table>
<p>これ以外にもあります。</p>
<p>自分はこれら以外はほぼ使わないので・・必要なら、こちらで。</p>
<p><iframe class="embed-card embed-webcard" style="display: block; width: 100%; height: 155px; max-width: 500px; margin: 10px 0px;" title="Scalars — NumPy v1.19.dev0 Manual" src="https://hatenablog-parts.com/embed?url=https%3A%2F%2Fnumpy.org%2Fdevdocs%2Freference%2Farrays.scalars.html" frameborder="0" scrolling="no"></iframe><cite class="hatena-citation"><a href="https://numpy.org/devdocs/reference/arrays.scalars.html">numpy.org</a></cite></p>
<p> </p>
<h4>Numpy配列を構築する</h4>
<p> </p>
<p>メソッドを使って初期値をセットしたNumpy配列を作ります。</p>
<p> </p>
<p><strong>すべてを0で初期化する</strong></p>
<pre class="prettyprint">np.zeros((2, 2), dtype=np.float32)</pre>
<p>結果は</p>
<blockquote>
<p>[[0. 0.] [0. 0.]]</p>
</blockquote>
<p> </p>
<p><strong>すべてを1で初期化する</strong></p>
<pre class="prettyprint"> np.ones((2, 2), dtype=np.float32)   </pre>
<p>結果は</p>
<blockquote>
<p>[[1. 1.] [1. 1.]]</p>
</blockquote>
<p> </p>
<p><strong>対角要素に1それ以外に0をセットして初期化する</strong></p>
<pre class="prettyprint">np.eye(3, dtype=np.float32)   </pre>
<p>結果は</p>
<blockquote>
<p>[</p>
<p>[1. 0. 0.]</p>
<p>[0. 1. 0.]</p>
<p>[0. 0. 1.]</p>
<p>]</p>
</blockquote>
<p> </p>
<p><strong>指定の値ですべてを埋めた配列を作る</strong></p>
<pre class="prettyprint">np.full((2, 2), 3.14)</pre>
<p>結果は</p>
<blockquote>
<p>[[3.14 3.14] [3.14 3.14]]</p>
</blockquote>
<p> </p>
<p><strong>乱数生成を使って初期化するもの</strong> </p>
<table>
<tbody>
<tr>
<th>例</th>
<th>説明</th>
<th>結果</th>
</tr>
<tr>
<td>
<pre class="prettyprint">np.random.random((2, 2))</pre>
</td>
<td>一様分布の乱数で初期化</td>
<td>[[0.83874852 0.25393169] [0.48973298 0.63288969]]</td>
</tr>
<tr>
<td>
<pre class="prettyprint">np.random.normal(1, 2, (2, 2))</pre>
</td>
<td>平均１<a class="keyword" href="http://d.hatena.ne.jp/keyword/%C9%B8%BD%E0%CA%D0%BA%B9">標準偏差</a>２の<a class="keyword" href="http://d.hatena.ne.jp/keyword/%C0%B5%B5%AC%CA%AC%C9%DB">正規分布</a></td>
<td>[[ 2.78714269 -1.10804489] [-0.13093131 1.58371071]]</td>
</tr>
<tr>
<td>
<pre class="prettyprint">np.random.randint(0, 10, (2, 2))</pre>
</td>
<td>指定範囲の一様分布の整数</td>
<td>[[0 3] [5 2]]</td>
</tr>
<tr>
<td>
<pre class="prettyprint">np.random.rand(2, 2)</pre>
</td>
<td>0.0以上1.0未満の乱数</td>
<td>[[0.2219319 0.16752553] [0.53437944 0.76555056]]</td>
</tr>
<tr>
<td>
<pre class="prettyprint">np.random.randn(2, 2)</pre>
</td>
<td>平均0分散1の乱数で初期化</td>
<td>[[-2.27146338 -0.00306964] [-1.04215926 1.20743357]]</td>
</tr>
</tbody>
</table>
<p>np.random のバリエーションは沢山あります。</p>
<p>もっと調べたい時はこちら。</p>
<p><iframe class="embed-card embed-webcard" style="display: block; width: 100%; height: 155px; max-width: 500px; margin: 10px 0px;" title="Legacy Random Generation — NumPy v1.19.dev0 Manual" src="https://hatenablog-parts.com/embed?url=https%3A%2F%2Fnumpy.org%2Fdevdocs%2Freference%2Frandom%2Flegacy.html" frameborder="0" scrolling="no"></iframe><cite class="hatena-citation"><a href="https://numpy.org/devdocs/reference/random/legacy.html">numpy.org</a></cite></p>
<p> </p>
<p><strong>for文なんかで少数の値を使いたいとき</strong></p>
<pre class="prettyprint">for x in np.arange(1.0,20.0, 0.2):
    print(x)
</pre>
<p>みたいに「np.arange」を使う。</p>
<p>結果は</p>
<blockquote>
<p>1.0<br />1.2<br />1.4<br />1.5999999999999999<br />1.7999999999999998</p>
</blockquote>
<p>みたいになります。</p>
<p> </p>
<p><strong><a class="keyword" href="http://d.hatena.ne.jp/keyword/python">python</a>のリストと相互変換する</strong></p>
<p><a class="keyword" href="http://d.hatena.ne.jp/keyword/python">python</a>のlistからNumpy配列にしたり、戻したりするやつです。</p>
<pre class="prettyprint">lstbase = [[1, 2, 3], [4, 5, 6]]
# listからNumpy配列
al1 = np.array(lstbase, dtype="float64")

# Numpy配列からlist
lstafter = al1.tolist()
</pre>
<p>リストに戻す時は、当然、Numpy配列のdtypeと互換性のある<a class="keyword" href="http://d.hatena.ne.jp/keyword/python">python</a>の型になります。</p>
<p> </p>
<h4>Numpy配列の属性を確認する</h4>
<p>Numpy配列の形状やサイズなどの情報を取り出します。</p>
<p>イメージしづらいので、こんな3行2列の配列の属性を取得する例を書きます。</p>
<blockquote>
<p>[[6.32486041 1.82922998]<br /> [1.91987168 0.40812655]<br /> [2.4821602 1.54720082]]</p>
</blockquote>
<p> </p>
<p><strong>配列の属性を確認する</strong></p>
<p>上記配列の名前は「a12」としています。</p>
<table>
<tbody>
<tr>
<th>書き方（配列をarとする）</th>
<th>意味</th>
<th>結果</th>
</tr>
<tr>
<td>a12.shape</td>
<td>配列形状のタプル</td>
<td>(3, 2)</td>
</tr>
<tr>
<td>a12.shape[0]</td>
<td>2次元の場合なら「行」</td>
<td>3</td>
</tr>
<tr>
<td>a12.shape[1]</td>
<td>2次元の場合なら「列」</td>
<td>2</td>
</tr>
<tr>
<td>a12.ndim</td>
<td>配列の次元数</td>
<td>2</td>
</tr>
<tr>
<td>a12.dtype</td>
<td>配列の型</td>
<td>float64</td>
</tr>
<tr>
<td>a12.size</td>
<td>配列の合計サイズ</td>
<td>6　：　3×2だから</td>
</tr>
<tr>
<td>a12.itemsize</td>
<td>各要素のバイト数</td>
<td>8　（バイト）</td>
</tr>
<tr>
<td>a12.nbytes</td>
<td>配列の合計バイト数</td>
<td>48（バイト：size×itemsize）</td>
</tr>
</tbody>
</table>
<p> のように取得できます。</p>
<p>他にもありますが、それはこちらで。</p>
<p><iframe class="embed-card embed-webcard" style="display: block; width: 100%; height: 155px; max-width: 500px; margin: 10px 0px;" title="The N-dimensional array (ndarray) — NumPy v1.19.dev0 Manual" src="https://hatenablog-parts.com/embed?url=https%3A%2F%2Fnumpy.org%2Fdevdocs%2Freference%2Farrays.ndarray.html" frameborder="0" scrolling="no"></iframe><cite class="hatena-citation"><a href="https://numpy.org/devdocs/reference/arrays.ndarray.html">numpy.org</a></cite></p>
<p> </p>
<p><strong>ndimとaxisについて</strong></p>
<p>ちなみに</p>
<ul>
<li>ndimは「次元数」</li>
<li>axisは「軸」</li>
</ul>
<p>です。</p>
<p>例えば、以下のような3行4列の配列は2次元配列なので、ndimは「2」です。</p>
<p>axis=0を指定すると列が軸、axis=1を指定すると行が軸です。</p>
<p><img src="https://cdn-ak.f.st-hatena.com/images/fotolife/a/arakan_no_boku/20200327/20200327101512.png" alt="f:id:arakan_no_boku:20200327101512p:plain" title="f:id:arakan_no_boku:20200327101512p:plain" class="hatena-fotolife" itemprop="image" /> </p>
<p> </p>
<h4>Numpy配列のループ</h4>
<p>Numpy配列の値をとりだして、forループを回す例です。</p>
<p>こんな感じの3行2列のNumpy配列を使ってやってみます。</p>
<blockquote>
<p>[[0.83751433 0.02594981]<br /> [2.8441739 3.17256053]<br /> [0.04499033 2.14228941]]</p>
</blockquote>
<p>上記配列は「a12」という名前で例を書いてます。</p>
<p>データだけを取り出す場合と、インデックスとデータ両方を取り出す場合があります。 </p>
<p> </p>
<p><strong>データだけを取り出すループ</strong></p>
<pre class="prettyprint">for x in np.nditer(a12):
    print(x)
</pre>
<p>出力結果はこんな感じでデータだけを順番に取得します。</p>
<blockquote>
<p>0.8375143297961567<br />0.025949813102027264<br />2.8441738981495615<br />3.1725605261342964<br />0.04499033206824665<br />2.142289407822542</p>
</blockquote>
<p> </p>
<p><strong>インデックスとデータを取り出すパターン</strong></p>
<p>インデックスは、multi_indexで参照できます。</p>
<pre class="prettyprint"> it = np.nditer(a12, flags=['multi_index'])
for x1 in it:
    print(it.multi_index, ":", x1)  
</pre>
<p>出力結果はこんな感じになります。 </p>
<blockquote>
<p>(0, 0) : 0.8375143297961567<br />(0, 1) : 0.025949813102027264<br />(1, 0) : 2.8441738981495615<br />(1, 1) : 3.1725605261342964<br />(2, 0) : 0.04499033206824665<br />(2, 1) : 2.142289407822542</p>
</blockquote>
<p> </p>
<h4>Numpy配列からのデータの取り出しとスライス</h4>
<p> </p>
<p>Numpy配列も<a class="keyword" href="http://d.hatena.ne.jp/keyword/Python">Python</a>のリストと同じように添え字で値を参照します。</p>
<p>上記例で使った配列「a12」をそのまま使うなら。</p>
<blockquote>
<p>a12[1,0] </p>
</blockquote>
<p> とすると</p>
<blockquote>
<p>2.8441738981495615</p>
</blockquote>
<p>が取得できる感じで。</p>
<p>同様に、スライスもできて、記述方法とルールも同じです。</p>
<blockquote>
<p>anylist[start:end:stride] </p>
<p>start：指定した添え字を含む、省略すると「0」（つまり添え字の先頭）</p>
<p>end：指定した添え字を含まない。省略すると「最後の要素まで」</p>
<p>stride：カウントアップする幅、省略すると「1」。-1だと逆順になる。</p>
</blockquote>
<p><iframe class="embed-card embed-blogcard" style="display: block; width: 100%; height: 190px; max-width: 500px; margin: 10px 0px;" title="Pythonのシーケンススライス構文のよく使う部分をまとめておく - &quot;BOKU&quot;のITな日常" src="https://hatenablog-parts.com/embed?url=https%3A%2F%2Farakan-pgm-ai.hatenablog.com%2Fentry%2F2018%2F11%2F29%2F090000" frameborder="0" scrolling="no"></iframe><cite class="hatena-citation"><a href="https://arakan-pgm-ai.hatenablog.com/entry/2018/11/29/090000">arakan-pgm-ai.hatenablog.com</a></cite></p>
<p> </p>
<p><strong>Numpy配列のスライスの例です。</strong></p>
<p>こういう配列データを使って例（結果列）を書いてます。。</p>
<blockquote>
<p>[[2 2 5 5]<br /> [4 3 0 2]<br /> [0 3 2 1]]</p>
</blockquote>
<p> この配列を「a7」という名前で参照してます。</p>
<table>
<tbody>
<tr>
<th>書き方</th>
<th>意味</th>
<th>結果</th>
</tr>
<tr>
<td>a7[2:, :]</td>
<td>3行目から取り出し</td>
<td>
<p>[</p>
<p>[0 3 2 1]</p>
<p>]</p>
</td>
</tr>
<tr>
<td>a7[:, :2]</td>
<td>2列目までとりだし</td>
<td>[[2 2] [4 3] [0 3]]</td>
</tr>
<tr>
<td>a7[::2, ::2]</td>
<td>行列共に１つおきに取り出し</td>
<td>[[2 5] [0 2]]</td>
</tr>
<tr>
<td>a7[:, ::-1]</td>
<td>列を逆順にソート</td>
<td>[[5 5 2 2] [2 0 3 4] [1 2 3 0]]</td>
</tr>
<tr>
<td>a7[::-1, :]</td>
<td>行を逆順にソート</td>
<td>[[0 3 2 1] [4 3 0 2] [2 2 5 5]]</td>
</tr>
<tr>
<td>a7[::-1, ::-1]</td>
<td>行と列を共に逆順にソート</td>
<td>[[1 2 3 0] [2 0 3 4] [5 5 2 2]]</td>
</tr>
<tr>
<td>a7[:, 1]</td>
<td>2列目をとりだす</td>
<td>[2 3 3]</td>
</tr>
<tr>
<td>a7[1, :]</td>
<td>2行目をとりだす</td>
<td>[4 3 0 2]</td>
</tr>
</tbody>
</table>
<p> </p>
<h4>Numpy配列のソート</h4>
<p> </p>
<p>スライスの応用の逆順ソートがでてきたので、続けて昇順にソートする方法です。</p>
<p>Numpyの昇順ソートは、np.sort()を使います。</p>
<p>ソート例の元にする配列は「a7」という変数名にします。</p>
<p>内容は以下です。</p>
<blockquote>
<p>[[5 4 8 6]<br /> [9 5 6 1]<br /> [2 0 3 0]]</p>
</blockquote>
<p> </p>
<p><strong>axisの指定無しにソートする</strong></p>
<pre class="prettyprint"> np.sort(a7)   
</pre>
<p>この結果はこうです。</p>
<blockquote>
<p>[[4 5 6 8]<br /> [1 5 6 9]<br /> [0 0 2 3]] </p>
</blockquote>
<p class="prettyprint">行単位で小さい数値が左から並ぶようにソートされています。</p>
<p class="prettyprint"><br /><br /><strong>axis=0を指定してソートする<br /></strong><br />axis=0は列を軸にするイメージでした。<br /><img src="https://cdn-ak.f.st-hatena.com/images/fotolife/a/arakan_no_boku/20200327/20200327101512.png" alt="f:id:arakan_no_boku:20200327101512p:plain" title="f:id:arakan_no_boku:20200327101512p:plain" class="hatena-fotolife" itemprop="image" /></p>
<pre class="prettyprint"> np.sort(a7, axis=0)</pre>
<p>この結果はこうです。 </p>
<blockquote>
<p> [[2 0 3 0]<br /> [5 4 6 1]<br /> [9 5 8 6]]</p>
</blockquote>
<p>列単位で小さい数値順に上から並び替えられているので、行でみるとシャッフルされたような感じになってます。</p>
<p> </p>
<p><strong>axis=1を指定してソートする</strong></p>
<p>axis=1は行を軸にするソートです。 </p>
<pre class="prettyprint">np.sort(a7, axis=1)
</pre>
<p>結果はこうです。 </p>
<blockquote>
<p> [[4 5 6 8]<br /> [1 5 6 9]<br /> [0 0 2 3]]</p>
</blockquote>
<p>行単位で左から小さい数字がならんでます。</p>
<p>つまり」、無指定の場合と同じjになります。 </p>
<p> </p>
<h4>Numpy配列の形状変更</h4>
<p> </p>
<p>Numpy配列を処理の都合にあわせて形状変更するのはよくあります。</p>
<p>それらの代表的なやり方だけまとめます。</p>
<p> </p>
<p><strong>一般的な形状変換パターン</strong></p>
<p>元になるNumpy配列はこんな１次元配列にします。</p>
<blockquote>
<p>[1 2 3 4 5 6 7 8 9]</p>
</blockquote>
<p>配列の名前は「aj1」としています。</p>
<p>これを「３×３」の二次元行列に変換するのは</p>
<pre class="prettyprint">aj33 = aj1.reshape((3, 3))
print(aj33)
</pre>
<p>返還後はこんな感じ</p>
<blockquote>
<p>[[1 2 3]<br /> [4 5 6]<br /> [7 8 9]] </p>
</blockquote>
<p> </p>
<p><strong>１次元から２次元の行へ</strong></p>
<p>これも頻繁に使います。</p>
<blockquote>
<p>[1 2 3 4 5 6 7 8 9]</p>
</blockquote>
<p>を</p>
<blockquote>
<p>[</p>
<p>[1 2 3 4 5 6 7 8 9]</p>
<p>] </p>
</blockquote>
<p>にするわけです。</p>
<p>当然ながら、上と同じように「reshape(1, 9)」とやってもできます。</p>
<p>でも、スライスで「np.newaxis」を使った以下のやり方を良く見ます。</p>
<p>元になる1次元配列は「aj1」で参照しています。</p>
<pre class="prettyprint">ajg2 = aj1[np.newaxis, :]
print(ajg2)
</pre>
<p>結果はreshape(1,3）とした場合と全く同じです。</p>
<blockquote>
<p>[</p>
<p>[1 2 3 4 5 6 7 8 9]</p>
<p>]  </p>
</blockquote>
<p> </p>
<p><strong>１次元から列ベクトルへ</strong></p>
<p>これは、ようするに。</p>
<blockquote>
<p>[1 2 3 4 5 6 7 8 9]</p>
</blockquote>
<p>を</p>
<blockquote>
<p>[[1]<br /> [2]<br /> [3]<br /> [4]<br /> [5]<br /> [6]<br /> [7]<br /> [8]<br /> [9]]</p>
</blockquote>
<p>にすることです。</p>
<p>当然ながら「reshape(9, 1)」とやってもできます。</p>
<p>でも、こちらもスライスで「np.newaxis」を使ったパターンをよく見ます。</p>
<p>元になる1次元配列は「aj1」で参照しています。</p>
<pre class="prettyprint">ajg2 = aj1[:, np.newaxis]
print(ajg2)
</pre>
<p>結果は「(9,1)でreshape()」した場合と同じです。</p>
<p> </p>
<p><strong>多次元から１次元に</strong></p>
<p>ようするに、例えば</p>
<blockquote>
<p>[[1 2 3]<br /> [4 5 6]<br /> [7 8 9]] </p>
</blockquote>
<p> を</p>
<blockquote>
<p>[1 2 3 4 5 6 7 8 9]</p>
</blockquote>
<p>に戻すことです。</p>
<p>flatten()を使います。</p>
<p>以下に一旦３×３にして、1次元に戻す例をやってます。</p>
<p>元の３×３配列を「aj33」として参照しています。</p>
<pre class="prettyprint">af = aj33.flatten()
print(af)
</pre>
<p>flatten()の結果はこんな感じ。 </p>
<blockquote>
<p>[1 2 3 4 5 6 7 8 9] </p>
</blockquote>
<p>いけてます。 </p>
<p> </p>
<p><strong>NUmpy配列を転置する</strong></p>
<p>転置とは、例えば「３×４」の配列を、「４×３」にするみたいに、行と列を入れ替えることです。</p>
<p>具体例でいえば</p>
<blockquote>
<p>[[4 4 3 1]<br /> [1 0 6 1]<br /> [8 6 6 6]]</p>
</blockquote>
<p>を</p>
<blockquote>
<p>[[4 1 8]<br /> [4 0 6]<br /> [3 6 6]<br /> [1 1 6]] </p>
</blockquote>
<p>にする感じです。</p>
<p>これは、Numpy配列を「a7」とすると</p>
<blockquote>
<p>転置後の配列 =<strong> a7.T</strong></p>
</blockquote>
<p> とすればいいです。 </p>
<p> </p>
<h4>Numpy配列の連結</h4>
<p> </p>
<p>例えば。</p>
<blockquote>
<p>[[4 3 5]<br /> [2 5 9]<br /> [0 1 8]]</p>
</blockquote>
<p>と</p>
<blockquote>
<p>[[5 2 3]<br /> [4 1 6]<br /> [3 5 5]]</p>
</blockquote>
<p>という２つの３×３配列を連結します。</p>
<p>便宜上、上を「g1」、下を「g2」とします。</p>
<p> </p>
<p><strong>配列を垂直（行が下に追加される感じ）で連結する</strong></p>
<p>２つやり方があります。</p>
<p>結果はどちらも同じです。</p>
<pre class="prettyprint"># 方法１
cg1 = np.concatenate([g1, g2])
# 方法２
cg3 = np.vstack([g1, g2])
</pre>
<p>どちらも結果は以下のように行追加の形になります。 </p>
<blockquote>
<p>[[4 3 5]<br /> [2 5 9]<br /> [0 1 8]<br /> [5 2 3]<br /> [4 1 6]<br /> [3 5 5]]</p>
</blockquote>
<p> </p>
<p><strong>配列を水平（列が後ろに追加される感じ）で連結する。</strong></p>
<p>こちらも2通りのやり方があり、結果はどちらも同じです。</p>
<pre class="prettyprint"># 方法１
cg2 = np.concatenate([g1, g2], axis=1)
# 方法２
cg4 = np.hstack([g1, g2])
</pre>
<p>結果は以下のように列が追加される感じになります。 </p>
<blockquote>
<p>[[4 3 5 5 2 3]<br /> [2 5 9 4 1 6]<br /> [0 1 8 3 5 5]] </p>
</blockquote>
<p> </p>
<h4>Numpy配列の分割</h4>
<p> </p>
<p>連結があれば、分割がある・・ということで。</p>
<p>さきほどの最<a class="keyword" href="http://d.hatena.ne.jp/keyword/%BD%AA%B7%EB">終結</a>果の</p>
<blockquote>
<p>[[8 7 6 4 9 9]<br /> [7 7 1 5 7 5]<br /> [9 4 3 6 0 0]]</p>
</blockquote>
<p>を分割してみます。</p>
<p> </p>
<p><strong>垂直方向（行単位でわかれていく感じ）に分割する</strong></p>
<p>とりあえず３つに分けます。</p>
<p>２つの方法があります。</p>
<pre class="prettyprint"># 方法１
d1, d2, d3 = np.vsplit(cg2, 3)
#　方法２
ds1, ds2, ds3 = np.split(cg2, 3, axis=0)
</pre>
<p>どちらも結果は同じです。</p>
<p>注意するのは分割する数にあわせ、左辺の受取側を増やさないといけないところです。</p>
<p>３つを続けて表示すると。</p>
<blockquote>
<p>[</p>
<p>[8 7 6 4 9 9]</p>
<p>]</p>
<p>[</p>
<p>[7 7 1 5 7 5]</p>
<p>]<br />[</p>
<p>[9 4 3 6 0 0]</p>
<p>]</p>
</blockquote>
<p> </p>
<p><strong>水平方向（列単位でわかれていく感じ）に分割する</strong></p>
<p> これも２つの方法があります。</p>
<pre class="prettyprint"># 方法１
h1, h2, h3 = np.hsplit(cg2, 3)

# 方法２
hs1, hs2, hs3 = np.split(cg2, 3, axis=1)
</pre>
<p>結果はこんな感じで列方向に３つにわかれます。</p>
<blockquote>
<p>[[8 7]<br /> [7 7]<br /> [9 4]]</p>
<p><br />[[6 4]<br /> [1 5]<br /> [3 6]]</p>
<p><br />[[9 9]<br /> [7 5]<br /> [0 0]] </p>
</blockquote>
<p> 左辺の受取側を分割する数にあわせて増やさないといけないのは同じです。</p>
<p> </p>
<h4>Numpy配列同士の演算</h4>
<p> </p>
<p>Numpyには「ユニバーサル関数（ufunc）」と呼ばれる<a class="keyword" href="http://d.hatena.ne.jp/keyword/%B1%E9%BB%BB%BB%D2">演算子</a>や関数が多く実装されていて、他の方法で行うより高速に処理できるようになってます。</p>
<p> </p>
<p><strong>まずは<a class="keyword" href="http://d.hatena.ne.jp/keyword/%B1%E9%BB%BB%BB%D2">演算子</a></strong></p>
<p> </p>
<p>Numpy配列同士の演算の例と計算結果を書いてます。</p>
<p>[[6 3]<br /> [4 6]]</p>
<p><br />[[2 2]<br /> [2 2]]</p>
<p> </p>
<p> 以下表の式の例は上の配列が「a」、下の配列を「b」と読み替えて結果を見てもらえるとわかりやすいです。</p>
<table>
<tbody>
<tr>
<th>算術<a class="keyword" href="http://d.hatena.ne.jp/keyword/%B1%E9%BB%BB%BB%D2">演算子</a></th>
<th>説明</th>
<th>式の例</th>
<th>結果例</th>
</tr>
<tr>
<th>＋</th>
<th>加算</th>
<th>a + b</th>
<th>[[8 5] [6 8]]</th>
</tr>
<tr>
<td>-</td>
<td>減算</td>
<td>a - b</td>
<td>[[4 1] [2 4]]</td>
</tr>
<tr>
<td>*</td>
<td>乗算</td>
<td>a * b</td>
<td>[[12 6] [ 8 12]]</td>
</tr>
<tr>
<td>/</td>
<td>除算(結果は少数）</td>
<td>a / b</td>
<td>[[3. 1.5] [2. 3. ]]</td>
</tr>
<tr>
<td>//</td>
<td>整数除算</td>
<td>a // b</td>
<td>[[3 1] [2 3]]</td>
</tr>
<tr>
<td>**</td>
<td>べき条</td>
<td>a ** b</td>
<td>[[36 9] [16 36]]</td>
</tr>
<tr>
<td>%</td>
<td>余剰（あまり）</td>
<td>a % b</td>
<td>[[0 1] [0 0]]</td>
</tr>
</tbody>
</table>
<p> </p>
<p><strong>比較<a class="keyword" href="http://d.hatena.ne.jp/keyword/%B1%E9%BB%BB%BB%D2">演算子</a></strong></p>
<p> </p>
<p><a class="keyword" href="http://d.hatena.ne.jp/keyword/%B1%E9%BB%BB%BB%D2">演算子</a>だけだとイメージしづらいので、以下のデータを使って例と結果を書きます。</p>
<blockquote>
<p>[[6 3 4]<br /> [4 6 3]]</p>
<p><br />[[-6 3 8]<br /> [-4 6 4]]</p>
</blockquote>
<p> 上を「a」、下を「c」として例と結果を書いています。</p>
<table>
<tbody>
<tr>
<th>算術<a class="keyword" href="http://d.hatena.ne.jp/keyword/%B1%E9%BB%BB%BB%D2">演算子</a>・関数</th>
<th>説明</th>
<th>式の例</th>
<th>結果例</th>
</tr>
<tr>
<td>==</td>
<td>等しい</td>
<td>a == c</td>
<td>[[False True False] [False True False]]</td>
</tr>
<tr>
<td>!=</td>
<td>等しくない</td>
<td>a != c</td>
<td>[[ True False True] [ True False True]]</td>
</tr>
<tr>
<td>&lt;</td>
<td>より小さい</td>
<td>a &lt; c</td>
<td>[[False False True] [False False True]]</td>
</tr>
<tr>
<td>&lt;=</td>
<td>より小さいか等しい</td>
<td>a &lt;= c</td>
<td>[[False True True] [False True True]]</td>
</tr>
<tr>
<td>&gt;</td>
<td>より大きい</td>
<td>a &gt; c</td>
<td>[[ True False False] [ True False False]]</td>
</tr>
<tr>
<td>&gt;=</td>
<td>より大きいか等しい</td>
<td>a &gt;= c</td>
<td>[[ True True False] [ True True False]]</td>
</tr>
<tr>
<td>np.any</td>
<td>条件に一致するものがひとつでもあればTrue</td>
<td>np.any(a == 4)</td>
<td>True</td>
</tr>
<tr>
<td>np.all</td>
<td>すべての値が条件に一致すればTrue</td>
<td>np.all(a == 4)</td>
<td>False</td>
</tr>
</tbody>
</table>
<p> </p>
<p><strong>関数</strong></p>
<p>主に集約や最大値・最小値を取得する関数です。</p>
<p>イメージしやすいように、以下の配列を引数にした結果を表に書いてます。</p>
<blockquote>
<p>[[-6 3 8]<br /> [-4 6 4]]</p>
</blockquote>
<p> 上記は「d」として表現しています。</p>
<p> </p>
<table>
<tbody>
<tr>
<th>組込み関数(例）</th>
<th>説明</th>
<th>結果</th>
</tr>
<tr>
<td>np.absolute(d)</td>
<td>絶対値</td>
<td>[[6 3 8] [4 6 4]]</td>
</tr>
<tr>
<td>np.sum(d)</td>
<td>配列全たの合計</td>
<td>11</td>
</tr>
<tr>
<td>d.sum(axis=0)</td>
<td>列単位の合計</td>
<td>[-10 9 12]</td>
</tr>
<tr>
<td>d.sum(axis=1)</td>
<td>行単位の合計</td>
<td>[5 6]</td>
</tr>
<tr>
<td>np.max(d)</td>
<td>配列全体の最大値</td>
<td>8</td>
</tr>
<tr>
<td>d.max(axis=0)</td>
<td>列単位の最大値</td>
<td>[-4 6 8]</td>
</tr>
<tr>
<td>d.max(axis=1)</td>
<td>行単位の最大値</td>
<td>[8 6]</td>
</tr>
<tr>
<td>np.argmax(d)</td>
<td>配列全体の最大値のインデックス</td>
<td>2</td>
</tr>
<tr>
<td>d.argmax(axis=0)</td>
<td>行単位の最大値のインデックス</td>
<td>[1 1 0]</td>
</tr>
<tr>
<td>d.argmax(axis=1)</td>
<td>列単位の最大値のインデックス</td>
<td>[2 1]</td>
</tr>
<tr>
<td>np.min(d)</td>
<td>配列全体の最小値</td>
<td>-6</td>
</tr>
<tr>
<td>d.min(axis=0)</td>
<td>列単位の最大値</td>
<td>[-6 3 4]</td>
</tr>
<tr>
<td>d.min(axis=1)</td>
<td>行単位の最大値</td>
<td>[-6 -4]</td>
</tr>
<tr>
<td>np.prod(d)</td>
<td>要素の籍を計算</td>
<td>13824</td>
</tr>
<tr>
<td>np.mean(d)</td>
<td>要素の平均値を計算</td>
<td>1.83333333333333</td>
</tr>
<tr>
<td>np.median(d)</td>
<td>要素の中央値を計算</td>
<td>3.5</td>
</tr>
<tr>
<td>np.dot(a, c)</td>
<td>ドット積</td>
<td>[[-72 48 92] [-66 57 80] [-66 57 80]]</td>
</tr>
</tbody>
</table>
<p>ドット積はわかりづらいので、補足のリンクです。</p>
<p><iframe class="embed-card embed-webcard" style="display: block; width: 100%; height: 155px; max-width: 500px; margin: 10px 0px;" title="ベクトルの内積や行列の積を求めるnumpy.dot関数の使い方" src="https://hatenablog-parts.com/embed?url=https%3A%2F%2Fdeepage.net%2Ffeatures%2Fnumpy-dot.html" frameborder="0" scrolling="no"></iframe><cite class="hatena-citation"><a href="https://deepage.net/features/numpy-dot.html">deepage.net</a></cite></p>
<p>ユニバーサル関数は他にも沢山あります。 </p>
<p><iframe class="embed-card embed-webcard" style="display: block; width: 100%; height: 155px; max-width: 500px; margin: 10px 0px;" title="Universal functions (ufunc) — NumPy v1.19.dev0 Manual" src="https://hatenablog-parts.com/embed?url=https%3A%2F%2Fnumpy.org%2Fdevdocs%2Freference%2Fufuncs.html%23ufunc" frameborder="0" scrolling="no"></iframe><cite class="hatena-citation"><a href="https://numpy.org/devdocs/reference/ufuncs.html#ufunc">numpy.org</a></cite></p>
<p>今のところ、こんな感じです。</p>
<p>ファンシーインデックスや構造化配列は、今のところ自分はあまり使う機会がないのと、ページが長くなりすぎるので省いてます。</p>
<p>他の<a class="keyword" href="http://d.hatena.ne.jp/keyword/%A4%DE%A4%C8%A4%E1%A5%DA%A1%BC%A5%B8">まとめページ</a>と同様、ぼちぼち書き足していこうかと思います。</p>
<p>ではでは。</p>
<p> </p>

