# 2021/09/23 nightingale

* データ可視化について学んでいると必ず話題になる、有名なナイチンゲールの図表というものがある。

![Nightingale-mortality](https://en.wikipedia.org/wiki/File:Nightingale-mortality.jpg)

* ナイチンゲールはクリミア戦争の際に、兵士の死者原因などの統計情報をきちんと整理し、次の事実を示した。戦場での死者より劣悪な病棟環境に因る病死者が多いこと、ナイチンゲールらがそれらを改善したことで、兵士の死亡率が改善したこと。これらは上記の図表によって分かりやすく説明された、と言われている。そうした実績を以て、彼女は1859年にイギリス王立統計学会の初の女性メンバーに選ばれ、後にはアメリカ統計学会の名誉メンバーに選ばれた(Wikipedia情報)。

* 当時は現代ほどチャートやグラフの手法が整理されておらず、彼女もあれこれ試行錯誤した結果のデータ可視化だったという。正直言って私も、この図表を初めて見たとき、その伝えたい情報を一目で把握することが出来なかった。多分彼女も、今なら普通の棒グラフや折れ線グラフにするのではないか、と思った。そこで現代に生きる彼女ならどう可視化するか検討できるように、ローデータをデジタル化しておく。私も今後、これらデータでの可視化を試みていきたい。

```text
yyyy,mm,StrengthOfTheArmy,Deaths(ZymoticDeseases),Deaths(WoundAndInjuries),Deaths(AllOtheCases),AROMP1000(ZymoticDeseases),AROMP1000(WoundAndInjuries),AROMP1000(AllOtherCases)
1854,04, 8571,   1,  0,  5,   1.4,  0  ,  7.0
1854,05,23333,  12,  0,  9,   6.2,  0  ,  4.6
1854,06,28333,  11,  0,  6,   4.7,  0  ,  2.5
1854,07,28722, 359,  0, 23, 150.0,  0  ,  9.6
1854,08,30246, 828,  1, 30, 328.5,  0.4, 11.9
1854,09,30290, 788, 81, 70, 312.2, 32.1, 27.7
1854,10,30643, 503,132,128, 197.0, 51.7, 50.1
1854,11,29736, 844,287,106, 340.6,115.8, 42.8
1854,12,32779,1725,114,131, 631.5, 41.7, 48.0
1855,01,32393,2761, 83,324,1022.8, 30.7,120.0
1855,02,30919,2120, 42,361, 822.8, 16.3,140.1
1855,03,30107,1205, 32,172, 480.3, 12.8, 68.6
1855,04,32252, 477, 48, 57, 177.5, 17.9, 21.2
1855,05,35473, 508, 49, 37, 171.8, 16.6, 12.5
1855,06,38863, 802,209, 31, 247.6, 64.5,  9.6
1855,07,42647, 382,134, 33, 107.5, 37.7,  9.3
1855,08,44614, 483,164, 25, 129.9, 44.1,  6.7
1855,09,47751, 189,276, 20,  47.5, 69.4,  5.0
1855,10,46852, 128, 53, 18,  32.8, 13.6,  4.6
1855,11,37853, 178, 33, 32,  56.4, 10.5, 10.1
1855,12,43217,  91, 18, 28,  25.3,  5.0,  7.8
1856,01,44212,  42,  2, 48,  11.4,  0.5, 13.0
1856,02,43485,  24,  0, 19,   6.6,  0  ,  5.2
1856,03,46140,  15,  0, 35,   3.9,  0  ,  9.1
```

* 出典はこちら <https://curiosity.lib.harvard.edu/contagion/catalog/36-990101646750203941> のPage 15、Table IIである。彼女の図表はPage 19にある。

* csvファイル単体ではこちら <https://pages.jpmap.jp/data/FlorenceNightingale_table2.csv>

* 各列は、年、月、兵力(兵士の数)、死亡者数(発酵病※不衛生な環境に因るものを指すと思われる)、死亡者数(外傷や負傷)、死亡者数(その他)、以降の列(AROMP1000と記載したもの)は既知の数値から計算可能であるが兵士1000人当たりの数値を年間で計算したものである。例えば1854/4の発酵病ならば、`1 / 8571 * 1000 * 12 = 1.4` といった具合。1855/1なんて1000を超えてしまうので、よく分からない数値なのだが、当時の軍隊を管理する上での一般的な指標のようなものだったのかもしれない。

* ナイチンゲールについて調べていると、大変興味深い。出典がメモ出来ていないのだが、「偉い人はどうせデータなんて見ないのだから、分かりやすく図示したもので説得する」的なことを言っていたり、`Notes on Nursing (1859)`という著書では、下記のような言っている。

```
If you look into the reports of trials or accidents, and especially of suicides, or into the medical history of fatal cases, it is almost incredible how often the whole thing turns upon something which has happened because "he," or still oftener "she," "was not there." But it is still more incredible how often, how almost always this is accepted as a sufficient reason, a justification; why, the very fact of the thing having happened is the proof of its not being a justification. The person in charge was quite right not to be "_there_," he was called away for quite sufficient reason, or he was away for a daily recurring and unavoidable cause: yet no provision was made to supply his absence. The fault was not in his "being away," but in there being no management to supplement his "being away." When the sun is under a total eclipse or during his nightly absence, we light candles. But it would seem as if it did not occur to us that we must also supplement the person in charge of sick or of children, whether under an occasional eclipse or during a regular absence.
```

* 適当に訳すと、`医療事故が起きた時にはよく、"彼や彼女(※看護者)"が"居なかった"ことが原因として言われがちである。(中略)しかし、過ちは彼らの不在でなく、マネジメントの不在にある。日食の時や太陽の居ない夜に、我々はろうそくを灯して明かりを補うのと同様、病人や子供に対する看護者の不在をきちんと補うということが行われていない。` みたいな感じで、現場の人員に責任を負わすのでなく、それらを管理する監督者のやり方がまずいのだ、と。ナイチンゲールの部下になって働きたい、、と思ってしまう。
