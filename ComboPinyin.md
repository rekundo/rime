# 宮保拼音

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-logo.png)

## 宮保拼音是啥

宮保拼音，洋文：Combo Pinyin，是用電腦鍵盤並擊輸入的拼音輸入法。

並擊（chording），即多指並用、同時擊鍵。

並擊輸入類似在鋼琴鍵盤上演奏和絃。一次擊鍵能傳達大量信息。
因此這種輸入方式節奏清晰、操作舒適，特別是能與中文一字一音的韻律同步。

宮保拼音的靈感來源——速錄技術，也是用並擊的方法在專業設備上快速錄入文字、記錄語音的。
爲求兼容最廣泛的電腦硬件和應用，宮保拼音設計了爲標準電腦鍵盤優化的並擊鍵位佈局，
並依託 [Rime 輸入法](rime.im) 開發了在多個電腦平臺上使用的軟件。

## 方案概要

宮保拼音用雙手同時操作鍵盤上的部分字母鍵、空格鍵，共計 20 鍵；
一次並擊會用到 1 至 6 鍵不等，可一擊輸入一個拼音音節。
在並擊輸入拼音之外，鍵盤上的其他操作如選字、輸入標點符號、使用功能鍵等與尋常的拼音輸入法無異。

按照電腦鍵盤盲打指法，並擊共用到七個手指，故該並擊佈局也稱「七指禪」。
除了標準鍵盤，宮保拼音也有適配分體鍵盤、九鍵鍵盤、速錄鍵盤的特定佈局。

[宮保拼音輸入方案](https://github.com/rime/rime-combo-pinyin) 是在 Rime 輸入法上實現該並擊法的配置。
輸入方案代碼爲 `combo_pinyin`。

Rime 輸入法的 `chord_composer` 組件支持對並擊鍵位的自定義，通過拼寫運算技術將並擊組合鍵映射爲拼音音節。

## 軟硬件需求

Rime 輸入法支持 Windows、Linux、macOS 等電腦操作系統。詳見 [Rime 輸入法](rime.im) 網站。

並擊操作要求鍵盤的性能滿足 6 鍵並擊無衝突（6KRO）。大多數機械鍵盤、電容式鍵盤都滿足此要求。

薄膜電路鍵盤普遍存在不同程度的按鍵衝突。宮保拼音的並擊鍵位儘量選用不易造成衝突的組合，可以在部分型號的薄膜鍵盤上正常使用，如 IBM Thinkpad、Mac 筆記本電腦的鍵盤等。但從觸感而言，膠碗-薄膜鍵盤不是運用並擊的最佳選擇。

機械鍵盤的衆多軸體類型中，輕線性軸是用於並擊的首選。
而觸發壓力較大或段落感極強的軸體，多鍵並擊手指易疲勞、得到不整齊的力反饋和聲音反饋，不推薦長時間使用。

## 先導知識

宮保拼音是以普通話的語音系統爲基礎設計的。他的按鍵於編碼並非依據漢語拼音的拼寫，而是直接對應普通話的音位。

考慮到大多數讀者不熟悉《漢語拼音方案》，這裏容我回顧該方案的主要內容，並對宮保拼音的語音基礎做出說明。

《漢語拼音方案》的完整文本，請參閱《新華字典》《現代漢語詞典》附錄、[教育部網站提供的影印版](http://www.moe.gov.cn/ewebeditor/uploadfile/2015/03/02/20150302165814246.pdf) 或 [維基文庫頁面](https://zh.wikisource.org/wiki/%E6%B1%89%E8%AF%AD%E6%8B%BC%E9%9F%B3%E6%96%B9%E6%A1%88)。

## 《漢語拼音方案》導讀

方案正文共有 5 個部分：一、字母表，二、聲母表，三、韻母表，四、聲調符號，五、隔音符號。

宮保拼音用左手輸入拼音音節中的聲母，用右手輸入拼音音節的韻母，同時擊發，奏出一個音節。
因此本文將詳細解讀〈聲母表〉〈韻母表〉。對其他章節做簡要說明。

### 字母表

〈字母表〉對拉丁字母（用做拼音字母）的名稱、順序、寫法做了定義和說明。

這裏要補充是，本文以及宮保拼音 3.0 版本各種圖表中字母的用法：

  * 宮保拼音鍵位或並擊組合鍵用大寫字母表示。如 `SHANE`。
  * 漢語拼音用小寫字母。爲明確拼寫法的種類，常用尖角括弧把拼音括起來，如 ⟨shang⟩。
  * QWERTY 鍵盤的字母鍵，本文用大寫字母指稱，但不套用代碼樣式。
  * 若敘述中同時提及鍵盤上的字母和宮保拼音鍵位，把宮保拼音鍵位及組合碼放在方括弧裏，以示區別。
    如：`[SHANE]` 須並擊鍵盤上的 S, D, K, L 及空格鍵。

### 聲調符號

定義了陰平、陽平、上聲、去聲四個聲調符號及標註方法。輕聲不標調。

本方案不輸入聲調。因此不再贅述。

### 隔音符號

⟨a, o, e⟩ 開頭的音節，與前面的音節之間用 `’` 隔開。

這個符號在連續書寫或連擊拼音字母時運用。

宮保拼音方案中，並擊提供了天然的音節界限，因此不需要額外輸入隔音符號。
技術上，軟件將在每個並擊所得的音節後自動加入隔音符號；輸入拼音後按退格鍵，也會以音節爲單位回退刪除拼音。

### 聲母表

原表在每個聲母下方用注音符號和漢字兩種方法註音，本文只節錄拼音部分。

|    |    |    |   |   |   |   |   |   |
|:--:|:--:|:--:|:-:|:-:|:-:|:-:|:-:|:-:|
| b  | p  | m  | f |   | d | t | n | l |
| g  | k  | h  |   |   | j | q | x |   |
| zh | ch | sh | r |   | z | c | s |   |
    
漢語拼音共設以上 21 個聲母。根據發音部位分爲六組。

在宮保拼音中，表中每一組發音部位相近的聲母，排列在同一行或同一列上；
相同的發音方法，如不送氣清音（全清）、送氣清音（次清）、鼻音（次濁）、邊音及擦音，也各有相同的指法。

### 韻母表

原表在每個韻母下方用注音符號和漢字兩種方法註音，本文只節錄拼音部分。

|     | i    | u    | ü   |
|:---:|:----:|:----:|:---:|
| a   | ia   | ua   |     |
| o   |      | uo   |     |
| e   | ie   |      | üe  |
| ai  |      | uai  |     |
| ei  |      | uei  |     |
| ao  | iao  |      |     |
| ou  | iou  |      |     |
| an  | ian  | uan  | üan |
| en  | in   | uen  | ün  |
| ang | iang | uang |     |
| eng | ing  | ueng |     |
| ong | iong |      |     |

表格第一行是 ⟨i, u, ü⟩ 三個韻母，他們可以用作介音，因此各自位於一豎行韻母的排頭。

表格左起第一豎行是不帶介音的韻母。按照順序，分別爲

  - 單元音⟨a, o, e⟩
  - 韻尾爲⟨-i⟩的雙元音⟨ai, ei⟩
  - 韻尾爲⟨-u⟩的雙元音⟨ao, ou⟩
  - 韻尾爲⟨-n⟩的前鼻音⟨an, en⟩
  - 韻尾爲⟨-ng⟩的後鼻音⟨ang, eng, ong⟩

他們與介音兩兩拼合，可得到表中的其他韻母。
通過聲母表，我們可以觀察到介音於韻的搭配關係，據此設計和理解並擊的組合鍵。

本文對上表需要補充的是：

1. 左列不帶介音的韻母，每個都是一個整體的符號，組成這些韻母的多個字母只描述大致的發音部位，不能直接按照字母拼出。
   特別是⟨ao, ong⟩兩個韻母中字母⟨o⟩對應的發音更接近元音⟨u⟩，而距元音⟨o⟩較遠。
   
2. 介音與韻的搭配，顯示了一定的規律性。
   如⟨ai, ei⟩只與介音⟨u⟩相拼、⟨ao, ou⟩只與介音⟨i⟩相拼；
   又如⟨o, e⟩在與介音的搭配上形成互補，⟨o⟩只在少量音節中與⟨e⟩形成對立且多爲語氣詞；
   與韻尾搭配，⟨ei, ou⟩也形成互補，因此有學者將⟨o, e⟩處理爲同一個音位。

3. ⟨ong, iong⟩兩個韻母，按照傳統的四呼分類、或是注音符號的拼法，分屬合口呼（⟨u⟩介音）、撮口呼（⟨ü⟩介音）；
   且⟨ueng, ong⟩這兩個韻母在與聲母的搭配上形成互補——⟨ueng⟩只拼零聲母或者說只用在自成音節的⟨weng⟩，而⟨ong⟩用於拼其他聲母。
   兩者無論從實際發音的近似性，還是歷史淵源，都可以視爲同一個韻母的條件變體。
   如果拋開方案擬定的寫，按照四呼的分類，可將⟨ong, iong⟩併入⟨eng⟩行合口呼（⟨u⟩介音）、撮口呼（⟨ü⟩介音）的位置。
   
至此，我們可以將普通話的韻母歸納爲 3 個介音、2 類韻核、4 種韻尾搭配組合的音位配列。

在宮保拼音的設計中，會運用我們對〈韻母表〉的分析，這可以幫助學習者理解並擊韻母的設置；
也會兼顧漢語拼音的拼寫法，用大家熟知的拼寫幫助記憶。

### 對韻母表的說明

方案在表後列出六條說明。這對理解《漢語拼音方案》和學習宮保拼音極爲重要，卻又是學校的拼音教育未涵蓋的內容，因此全文摘抄，並做說明。

>（1）“知、蚩、詩、日、資、雌、思”等七個音節的韻母用 i，即：知、蚩、詩、日、資、雌、思等字拼作 zhi，chi，shi，ri，zi，ci，si。
>
>（2）韻母ㄦ寫成 er，用作韻尾的時候寫成 r。例如：“兒童”拼作 ertong，“花兒”拼作 huar。
>
>（3）韻母ㄝ單用的時候寫成 ê。

這三條介紹了未列入表中的韻母：

  - “知、蚩、詩、日、資、雌、思”等七個音節的韻母，也可叫做舌尖元音。
    他的發音不同於⟨i⟩，且傳統音韻學將其分類爲開口呼而非齊齒呼。大致可以放入表中左上角空白的位置。
    本文爲了區別於⟨i⟩，把舌尖元音標記爲⟨ï⟩。注意這個符號不是《漢語拼音方案》的一部分。
    
  - 韻母⟨er⟩只獨用，不與聲母搭配。
    從歷史上看，⟨er⟩是從舌尖元音分化出來，也與舌尖元音形成互補。因此也可以併入左上角的單元格。
    
  - 韻母⟨ê⟩極少單用，但與介音相拼得⟨ie, üe⟩兩個韻母。反而是⟨e⟩不能與任何介音拼合。可知方案視⟨ê⟩爲⟨e⟩的變體。

>（4）i行的韻母，前面沒有聲母的時候，寫成 yi（衣），ya（呀），ye（耶），yao（腰），you（憂），yan（煙），yin（因），yang（央），ying（英），yong（雍）。\
>u行的韻母，前面沒有聲母的時候，寫成 wu（烏），wa（蛙），wo（窩），wai（歪），wei（威），wan（彎），wen（溫），wang（汪），weng（翁）。\
>ü行的韻母，前面沒有聲母的時候，寫成 yu（迂），yue（約），yuan（冤），yun（暈）；ü 上兩點省略。\
>ü行的韻母跟聲母 j，q，x 拼的時候，寫成 ju（居），qu（區），xu（虛），ü上兩點也省略；但是跟聲母 n，l 拼的時候，仍然寫成 nü（女），lü（呂）。
>
>（5）iou，uei，uen 前面加聲母的時候，寫成 iu，ui，un。例如 niu（牛），gui（歸），lun（論）。

這兩條介紹了漢語拼音韻母在音節中的拼寫規則。請熟知：

  - ⟨i, u, ü⟩與各種聲母拼合時的改寫方法、拼音字母⟨y, w⟩的使用；
  - ⟨iou, uei, uen⟩自成音節時（改寫首字母）以及與其他聲母拼合時（省略中間的元音字母）所得的兩種拼寫形式。
  
宮保拼音不使用這些拼寫規則——同一個韻母在不同的音節裏有一致的鍵位和指法。

>（6）在給漢字注音的時候，爲了使拼式簡短，ng可以省作ŋ。

⟨ng⟩ 是一個韻尾。包含⟨ng⟩的韻母，其發音部位較靠後，因此叫做「後鼻音」。本文將該韻尾表記爲⟨-ng⟩。

熟知了漢語拼音方案中的聲母、韻母和拼寫規則，再學習宮保拼音的聲母、韻母，就會思維透徹，條理清晰，事倍功半。

## 《宮保拼音》並擊方案詳解
### 鍵盤佈局

![鍵盤佈局圖](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-layout.png)

宮保拼音「七指禪」佈局，用到鍵盤左手半區的 W E R T, S D F G, X C V B 等字母鍵、右手半區的 U I O, J K L, M 等字母鍵，以及右手拇指操作的空格鍵。小指和左手拇指不用。

本文的圖示只包含上述並擊用到的按鍵所在的行、列。

鍵盤上的 F, J 兩鍵是盲打定位鍵，帶有凸點，在圖上有所顯示。
學習者可以憑借兩個定位鍵確定其他按鍵的位置。

### 鍵位與指法

![指法圖](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-touch-typing-guide.png)


沿中軸線，上方的三行按鍵分爲左右兩個半區。

圖中標在鍵位上方、側方的數字是手指的解剖學編號，拇指爲 1 號手指，食指爲 2 號手指，依此類推。

左手畔的 12 個聲母鍵用左手 2, 3, 4 指操作。其中 2 號指負責兩列，與盲打指法相同。

這 12 個聲母鍵表示與其字母相同的聲母。可分爲四個區域。按照聲母表順序有：

  - `[B][P][F]` 位於第三行，對應鍵盤上的字母 V, B, C
  - `[D][T][L]` 位於第一行，對應鍵盤上的字母 R, T, E
  - `[G][K][H]` 位於第二行，對應鍵盤上的字母 F, G, D
  - `[Z][C][S]` 位於縱向第一列，對應的鍵盤字母 X, W, S
  
其他 9 個未分配鍵位的聲母用並擊輸入。

各個縱列的分佈規律是：

  - 2 號指轄`[B][D][G]`、`[P][T][K]`。
    不送氣清音⟨b, d, g⟩位於盲點所在的列；送氣清音⟨p, t, k⟩在距盲點較遠的一列。
  - 3 號指轄`[F][L][H]`，即各行聲母中的邊音、擦音⟨f, l, h⟩。
  - 4 號指轄`[Z][C][S]`，即⟨z, c, s⟩這組聲母。

右手畔的韻母多用並擊。設有以下鍵位。

  - 2 號指轄 `[I][U][Ü]`，對應鍵盤上的字母 J, U, M
  - 1 號指轄 `[A]`，用在包含元音字母 ⟨a⟩ 的並擊韻母裏，這在所有韻母中佔到近半數。
  - 4 號指轄 `[O][E]`
  - 3 號指轄 `[N]` 表示韻尾 ⟨-n⟩、`[R]` 表示韻母 ⟨er⟩。用於並擊時，`[R]` 兼表韻尾 ⟨-i⟩ 或 ⟨-u⟩。
    兒化韻裏⟨-r⟩做韻尾；雖然本方案不支持兒化韻，但因爲這層關係，將 `[R]` 鍵歸入韻尾之列，並統轄非鼻音韻尾。

與鍵盤上字母重合的宮保拼音鍵位有 `[S] [T] [U] [O]`。

### 並擊鍵序

宮保拼音的按鍵，並擊時不論按下的先後順序；然而在書寫並擊組合時，組合鍵要按照特定的順序排列以方便閱讀。

所有按鍵的書寫順序如下。左右兩個半區以 `-` 爲界。
各縱列從左到右排列，唯有 `A` 穿插到介音與韻尾之間的位置。

    SCZHLFGDBKTP-IUÜANREO

### 並擊鍵位濃縮圖

![並擊鍵位](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-chords.png)

### 並擊聲母

左手半區設有 3 組、共計 9 個並擊聲母。

#### zh, ch, sh

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-zh-ch-sh-ou-eng.png)

4 號指、3 號指並擊 `[Z][C][S]` 與右邊相鄰的鍵，得到並擊聲母⟨zh, ch, sh⟩。

  - `ZF` = ⟨zh⟩
  - `CL` = ⟨ch⟩
  - `SH` = ⟨sh⟩

`[ZH] [CH]` 需要錯行，指法不便利，故借用了與 `[H]` 同一列的鍵，改爲 `[ZF] [CL]`。

#### m, n, r

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-m-n-r-uei-in.png)

3 號指、2 號指並擊同一行的相鄰兩鍵，得到並擊聲母⟨m, n, r⟩。

  - `FB` = ⟨m⟩
  - `LD` = ⟨n⟩
  - `HG` = ⟨r⟩

⟨m⟩用同組的聲母 `[F][B]` 並擊，⟨n⟩用同組的聲母 `[L][D]` 並擊，二者皆是各組聲母中的鼻音。

⟨r⟩與`[H][G]`沒有直接關聯，他演化自中古漢語裏屬於鼻音聲母的日母，故與鼻音聲母並列。

#### j, q, x

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-j-q-x-iou-yun.png)

⟨j, q, x⟩復用 `[G][K][H]` 三鍵。兩組聲母在聲韻搭配上形成互補：
⟨g, k, h⟩只拼開口呼（無介音）、合口呼（⟨-u⟩介音）的韻母，而⟨j, q, x⟩只拼齊齒呼（⟨-i⟩介音）、撮口呼（⟨-ü⟩介音）的韻母。

這一規律反映在並擊指法上即爲：`[G][K][H]` 與 `[I]` 或 `[Ü]` 並擊時，代表聲母⟨j, q, x⟩。

#### 尖團音

分尖團的方言，`[G][K][H]` 與 `[I][Ü]` 並擊表示團音⟨j, q, x⟩，
用 `[Z][C][S]` 與 `[I][Ü]` 並擊，表示與其對立的尖音。

普通話不分尖團，不用這組並擊聲母。

### 並擊韻母

右手半區大量設置並擊韻母。

#### 單韻母

8 個韻母鍵各自代表一個韻母：

  - `[I]` = ⟨i⟩
  - `[U]` = ⟨u⟩
  - `[Ü]` = ⟨ü⟩
  - `[A]` = ⟨a⟩，單擊爲空格
  - `[O]` = ⟨o⟩，一些音節中可替代⟨ou⟩
  - `[E]` = ⟨e⟩，一些音節中可替代⟨ei⟩
  - `[R]` = ⟨er⟩，並擊時表示舌尖元音⟨ï⟩，但通常省略
  - `[N]` = ⟨en⟩

介音與韻的組合，無一例外用 `[I][U][Ü]` 與其他韻母並擊。

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-uo-ie.png)

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-io-yue.png)

`[A]` 鍵單擊爲空格鍵，用於輸入空格、選字等操作。
  
![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-space.png)

音節⟨'a⟩用特定並擊組合 `[AE]` 輸入。

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-a-ia-ua.png)

#### 複韻母

雙元音⟨ai, ei, ou⟩用 `[R]` 鍵與 `[A][E][O]` 並擊。`[R]` 代表韻尾 ⟨-i⟩ 或 ⟨-u⟩。
  
雙元音⟨ao⟩用`[AO]`並擊。韻尾的⟨-u⟩用與拼寫一致的 `[O]` 表示。

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-ai-ao-an.png)

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-ei-uen.png)

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-zh-ch-sh-ou-eng.png)
  
雙元音與介音相拼，得⟨iao, iou, uai, uei⟩。
 
![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-iao-yuan.png)

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-j-q-x-iou-yun.png)

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-uai-ian.png)

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-m-n-r-uei-in.png)

⟨iou⟩省略中間的元音字母，並擊 `[IR]`；
⟨uei⟩省略中間的元音字母，並擊 `[UR]`。

不同於漢語拼音的拼寫規則，上述省略形式也用於零聲母音節⟨you, wei⟩。

#### 鼻韻母

`[N]` 爲韻尾 ⟨-n⟩，`[NE]` 爲韻尾 ⟨-ng⟩。
不與其他元音字母鍵並擊時，二者分別代表韻母⟨en, eng⟩，省略拼音字母⟨e⟩。

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-i-u-yu-er-en-o-e.png)
    
![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-zh-ch-sh-ou-eng.png)

按照四呼拼讀，⟨en, in, uen, ün⟩分別爲並擊 `[N], [IN], [UN], [ÜN]`。

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-m-n-r-uei-in.png)

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-ei-uen.png)

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-j-q-x-iou-yun.png)

按照四呼拼讀，⟨eng, ing, ueng/ong, iong⟩分別爲並擊 `[NE], [INE], [UNE], [ÜNE]`。
    
`[UNE]` = ⟨ueng/ong⟩，需要錯行並擊，可借用 `[U]` 所在行的 `[RO]` 兩鍵代替 `[NE]`。於是有：

`[URO]` = ⟨ueng/ong⟩。相鄰三鍵並擊，指法便利。也可以看作爲⟨ong⟩的拼寫而設置的並擊組合鍵。

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-ing-ong.png)
    
`[ÜNE]` = ⟨iong⟩，可以把三鍵同時上移到 `[IRO]` 的位置，使該並擊韻母更符合拼寫。

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-iong.png)

`[A]` 與 `[N]` 並擊爲韻母⟨an⟩。

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-ai-ao-an.png)

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-uai-ian.png)

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-uan.png)

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-iao-yuan.png)

`[A]` 與 `[NE]` 並擊爲韻母⟨ang⟩。

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-ang.png)

`[A]` 與 `[INE], [URO]` 並擊，分別爲韻母⟨iang, uang⟩。

![](https://github.com/rime/home/blob/master/images/combo-pinyin-v3/combo-pinyin-iang-uang.png)

### 韻母的缺省與通借

通借，即通假。是速記技術中，復用基本符號、利用空閒編碼空間、簡化速記符號的方法。

前文已經介紹過如將 `[ZH], [CH]` 優化爲指法便利的 `[ZF], [CL]`，將 `[UNE]` 中的 `[NE]` 改爲與 `[U]` 在同一行的 `[RO]`。
這些都是通借的例子。通借的前提是在符合一定規律的條件下，某個並擊編碼不使用；此時即可借作他用。

通過以下手段，可進一步簡化並擊的指法。

#### 缺省韻母

並擊輸入的特點是，一次並擊輸入一個（或多個）完整音節。

因此，當只擊出韻母、聲母空缺時，表示拼零聲母，或者說韻母自成音節。

只擊出聲母、韻母空缺時，由於韻母是拼音輸入法裏音節的必要成分，故添加一個缺省韻母，與聲母拼成一個常用音節。
以下按照聲母表分組列出。

    [B] = ⟨bu⟩
    [P] = ⟨pu⟩
    [F] = ⟨fu⟩
    [FB] = ⟨me⟩

該組聲母的呼讀音⟨bo, po, mo, fo⟩對應的音節不十分常用，因而規定缺省韻母的音節爲⟨bu, pu, fu⟩和⟨me⟩，對應「不、麼」等常用字。

    [D] = ⟨de⟩
    [T] = ⟨te⟩
    [L] = ⟨le⟩
    [LD] = ⟨ne⟩

該組聲母的呼讀音⟨de, te, ne, le⟩用於輸入語助詞「的、了」等常用字。

    [G] = ⟨ge⟩
    [K] = ⟨ke⟩
    [H] = ⟨he⟩

該組聲母的呼讀音⟨ge, ke, he⟩皆常用，故設爲缺省韻母。

⟨j, q, x⟩必須與韻母並擊，因此不設缺省韻母。

    [ZF] = ⟨zhi⟩
    [CL] = ⟨chi⟩
    [SH] = ⟨shi⟩
    [HG] = ⟨ri⟩

    [Z] = ⟨si⟩
    [C] = ⟨si⟩
    [S] = ⟨si⟩

這兩組聲母的缺省韻母爲舌尖元音⟨ï⟩。

因爲在音節中的舌尖元音全部是缺省韻母，所以表示舌尖元音的 `[R]` 通常省略。

#### O 通借爲 ou

⟨o⟩不帶介音時，只能拼出極少數的音節，且以語氣詞爲主。聲韻搭配存在許多未利用的空位。
下列音節中借用 `[O]` 鍵表示韻母⟨ou⟩。

    [DO] = ⟨dou⟩
    [TO] = ⟨tou⟩
    [LO] = ⟨lou⟩
    [LDO] = ⟨nou⟩
    
    [GO] = ⟨gou⟩
    [KO] = ⟨kou⟩
    [HO] = ⟨hou⟩
    
    [ZFO] = ⟨zhou⟩
    [CLO] = ⟨chou⟩
    [SHO] = ⟨shou⟩
    [HGO] = ⟨rou⟩
    
    [ZO] = ⟨zou⟩
    [CO] = ⟨cou⟩
    [SO] = ⟨sou⟩
  
然而，⟨pou, mou, fou⟩與⟨po, mo, fo⟩存在對立，這組聲母拼⟨ou⟩不可以借用 `[O]`。

#### E 通借爲 ei

⟨e⟩不帶介音時，是⟨d⟩組、⟨g⟩組聲母以及⟨m⟩的缺省韻母；其他⟨b⟩組聲母不與⟨e⟩相拼。
於是，這三組聲母可以借用 `[E]` 鍵表示拼韻母⟨ei⟩。

    [BE] = ⟨bei⟩
    [PE] = ⟨pei⟩
    [FE] = ⟨fei⟩
    [FBE] = ⟨mei⟩

    [DE] = ⟨dei⟩
    [TE] = ⟨tei⟩
    [LE] = ⟨lei⟩
    [LDE] = ⟨nei⟩
    
    [GE] = ⟨gei⟩ 
    [KE] = ⟨kei⟩ 
    [HE] = ⟨hei⟩ 

然而，⟨zhei, shei, zei, cei, sei⟩與⟨zhe, she, ze, ce, se⟩存在對立，這組聲母拼⟨ei⟩不可以借用 `[E]`。

#### 總結 O 與 E 的通借規則

`[O], [E]` 分別是對 `[RO], [RE]` 的簡省。

`[O], [E]` 通借爲韻母⟨ou, ei⟩，有一定的適用條件：

 - 這裏討論的韻母都不帶介音，即直接與聲母拼；有介音時，`[O], [E]` 只表示⟨o, e⟩。
 - 按照聲母表一組一組地觀察；
 - 若一組聲母可同時拼⟨o⟩與⟨ou⟩，且兩者都不是該組聲母的缺省韻母，則不得通借；
 - 若一組聲母可同時拼⟨e⟩與⟨ei⟩，且兩者都不是該組聲母的缺省韻母，則不得通借。

熟悉聲、韻配合規律後，易知：

1. ⟨b⟩組聲母可同時拼⟨o⟩與⟨ou⟩，且兩者不是缺省韻母，故 `[O]` 不得通借爲⟨ou⟩。
2. ⟨l⟩雖然可以拼出⟨lo⟩與⟨lou⟩，但⟨lo⟩只表示語氣詞，並且該組聲母再無可以與⟨o⟩拼讀者；
   爲了充分利用簡短的並擊碼，本方案特將這兩個音節合併，從而允許 `[O]` 與⟨d⟩組聲母並擊時通借爲韻母⟨ou⟩。
3. `[O]` 與⟨d⟩組、⟨g⟩組、⟨zh⟩組、⟨z⟩組聲母並擊均可表示韻母⟨ou⟩。
4. ⟨zh⟩組、⟨z⟩組聲母可同時拼⟨e⟩與⟨ei⟩，且兩者不是缺省韻母，故 `[E]` 不得通借爲⟨ei⟩。 
5. ⟨b⟩組聲母不拼韻母⟨e⟩；⟨d⟩組、⟨g⟩組有缺省韻母⟨e⟩，故 `[E]` 與⟨b⟩組、⟨d⟩組、⟨g⟩組聲母並擊時，通借爲韻母⟨ei⟩。
6. ⟨j⟩組聲母不能拼相關的韻母。

列表如下：

|       | ⟨b⟩組 | ⟨d⟩組 | ⟨g⟩組 | ⟨zh⟩組 | ⟨z⟩組 |
|-------|-------|-------|-------|--------|-------|
| `[O]` | ⟨o⟩   | ⟨ou⟩  | ⟨ou⟩  | ⟨ou⟩   | ⟨ou⟩  |
| `[E]` | ⟨ei⟩  | ⟨ei⟩  | ⟨ei⟩  | ⟨e⟩    | ⟨e⟩   |

如果不熟悉，韻母⟨ou, ei⟩可以一律並擊 `[RO], [RE]`，在今後的使用中逐漸總結發現可通借的規律，達到簡省擊鍵的目的。

## 結語

至此，宮保拼音的並擊方案介紹完了。
這是並擊技術與電腦軟硬件、與漢語言文字的美妙結合。

要享受並擊輸入的便利，輕鬆自如地鍵字，須在理解和記憶本方案的基礎上，通過不斷的練習形成字音到並擊鍵位的條件反射。

本文用到的所有圖表彙編成卷，供用家參考。
https://github.com/rime/home/blob/master/manual/combo-pinyin-cheatsheet.pdf

輸入技術，亦無他，惟手熟耳。
Rime 輸入法多平臺可及，宮保拼音的並擊方案對電腦鍵盤做了最大程度的兼容，於是用家初步掌握後即可在工作、學習中充分鍛鍊，達到慣用。

宮保拼音還在探索適配特殊配列鍵盤、加入縮略碼等速錄的機制。有關這些方向的發展，請關注 [rime/rime-combo-pinyin](https://github.com/rime/rime-combo-pinyin) 代碼庫的更新。

祝你打字愉快！
