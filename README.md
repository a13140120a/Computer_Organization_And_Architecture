# Computer_Organization_And_Architecture

* ## [基礎概念](#001) #
* ## [數據表示法](#002) #
* ## [布林代數與數位邏輯](#003) #
* ## [MARIE](#004) #
  
****
<h1 id="001">基礎概念</h1> 

* ## [組織與結構](#0011) #
* ## [計算機主要元件](#0012) #
* ## [容量單位](#0013) #
* ## [摩爾定律](#0014) #
* ## [計算機階層](#0015) #
* ## [雲服務](#0016) #
* ## [von Neumann](#0017) #


<h2 id="0011">組織與結構</h2> 

* 計算機組織(computer organization):
  * 物理相關面向，探討控制訊號、訊號傳遞方式與記憶體型態等議題。
* 計算機結構(computer architecture):
  * 邏輯抽象層面，注重計算機的架構與行為，內容包含指令集與格式、運作碼、數據型態暫存器數量與型態、定址模式、主記憶體存取方法與各種I/O機制等元素。 

<h2 id="0012">計算機主要元件</h2> 

  1.  cpu   
  2.  memory  
  3.  I/O device  
  4.  
<h2 id="0013">容量單位</h2> 
 
  字首大寫表示2的次方(K, M G)，小寫表示10的次方，大寫B代表Byte，小寫b代表bit,
  |符號| 說明 |
  |--- | --- |
  |K| 1KB = 1 * 2^10 Bytes, 1Kb = 1 * 2^10 bits|
  |M| 1MB = 1 * 2^20 Bytes, 1Mb = 1 * 2^20 bits|
  |G| 1GB = 1 * 2^30 Bytes, 1Gb = 1 * 2^30 bits|
  |k| 1kB = 1 * 10^3 Bytes, 1Kb = 1 * 10^3 bits|
  |m| 1mB = 1 * 10^6 Bytes, 1mb = 1 * 10^6 bits|
  |g| 1gB = 1 * 10^9 Bytes, 1gb = 1 * 10^9 bits|
  
<h2 id="0014">摩爾定律</h2> 

* 積體電路上可容納的電晶體數目，約每隔兩年便會增加一倍  [(wiki)](https://zh.wikipedia.org/wiki/%E6%91%A9%E5%B0%94%E5%AE%9A%E5%BE%8B)

<h2 id="0015">計算機階層</h2> 

  |level | 說明 | e.g. |
  |--- | --- | --- |
  |6| User | 程式 |
  |5| 高階語言 | C++、Java etc. |
  |4| 組合語言 | 組合語言 |
  |3| 系統軟體 | OS、程式庫 |
  |2| 機器 | 指令集(ISA) |
  |1| 控制 | microcode、hardwired |
  |0| 數位邏輯 | 電路、閘(Gate) |
  
<h2 id="0016">雲服務</h2> 

* 基礎架構即服務[(IaaS)](https://azure.microsoft.com/zh-tw/overview/what-is-iaas/#overview): 包含level 0、1、2:  
      適用於 "當公司業務主要用於軟體研發時" 的情境
      EX: Amazon EC2, Google Compute Engine, Minecrosoft Azure Service Platform, HP Cloud
* 平台即服務[(PaaS)](https://azure.microsoft.com/zh-tw/overview/what-is-paas/): 包含level 3、4、5:  
      提供伺服器硬體、作業系統、資料庫服務、資安組件、備援及回復功能。
      比LaaS有更大的對應用程式控制能力，可建構自己的應用程式
      EX: Google App Engine, Mivrosoft Windows Azure Cloud Service
* 軟體即服務[(SaaS)](https://azure.microsoft.com/zh-tw/overview/what-is-saas/): 包含level 6  
      供應商提供可以透過網際網路提供整個應用而不需再使用者組件，消費者不需要維護或關心任何基本架構的事。
      EX: Gmail, Dropbox, Netflix

<h2 id="0017">von Neumann(馮紐曼)</h2> 

* [見wiki](https://zh.wikipedia.org/wiki/%E5%86%AF%C2%B7%E8%AF%BA%E4%BC%8A%E6%9B%BC%E7%BB%93%E6%9E%84)
* [history](https://pansci.asia/archives/194219)
* von Numann execution cycle(馮紐曼週期): [見4.9](#0049)

<h1 id="002">數據表示法</h1> 

* ## [基礎概念](#0021) #
* ## [有號整數表示法](#0022) #
* ## [Booth's multiplication algorithm](#0023) #
* ## [rotation](#0024) #
* ## [浮點表示法](#0025) #
* ## [字元符號](#0026) #
* ## [data compression](#0027) #
* ## [Error detecting and Error correcting](#0028) #


<h2 id="0021">基礎概念</h2> 

* bit(位元): 電腦中最基本的單位，是電路中的開(高電位) 或關(低電位)的狀態
* byte(位元組): 8個bits
* word(字組): 表示特定環境下處理起來最有效率的單位，大小不一定是幾個bit，看環境決定。
* overflow(溢位): 超過指定bit 能夠表示的範圍，例如4個bit的2's Complement表示法0101(5)與0011(3)相加結果是(-8)為溢位，進位不代表溢位。

<h2 id="0022">有號整數表示法</h2> 

* Unsigned Representation(無號數表示法): Unsigned就是沒有符號的意思，因為沒有符號，所以不會有負數。
* 而Signed就是有符號的意思，所以會有分負數與正數，Singed Representation 較常見的又分為以下幾種
  * sign-magnitude representation: 顧名思義就是 符號-大小 的表示法，第一個bit控制正負，其他的bit表示大小。  
    => 最基礎的負數表達方法，電路設計困難，有兩個0的表示法。
  * 1's Complement: 1轉0，0轉1，進位要再 + 1。  
    => 好處是設計電路簡單，缺點有兩個0的表示法
  * 2's Complement: 1's Complement + 1。  
    => 設計電路簡單，改善有兩個0的表示法問題，缺點是能表示的正負範圍不對稱，ex: 4bit = -8~7
  * Excess: 偏移值2的n-1次方-1為中心點0做計算。
  * [詳細內容](https://medium.com/@a131401203/%E4%B8%AD%E6%96%87%E7%B3%BB%E4%B9%8B%E6%95%B8%E6%93%9A%E8%A1%A8%E7%A4%BA%E6%B3%95-4c833a17c803)

<h2 id="0023">Booth's multiplication algorithm</h2> 

* [wiki](https://zh.wikipedia.org/wiki/%E5%B8%83%E6%96%AF%E4%B9%98%E6%B3%95%E7%AE%97%E6%B3%95)(後續補上)

<h2 id="0024">rotation</h2> 

* 向右移一位為乘2，向左移一位則除2。

<h2 id="0025">浮點表示法</h2> 

*  [浮點表示法](https://medium.com/@a131401203/%E4%B8%AD%E6%96%87%E7%B3%BB%E4%B9%8B%E6%95%B8%E6%93%9A%E8%A1%A8%E7%A4%BA%E6%B3%95%E7%AC%AC%E4%BA%8C%E9%9B%86%E4%B9%8B%E6%B5%AE%E9%BB%9E%E8%A1%A8%E7%A4%BA%E6%B3%95-2a414e50cf28)

<h2 id="0026">字元符號</h2> 

 * [BCD](https://zh.wikipedia.org/wiki/%E4%BA%8C%E9%80%B2%E7%A2%BC%E5%8D%81%E9%80%B2%E6%95%B8) (uncompressed or zoned): 未壓縮的BCD碼，以八位元為一個單位表達一個十進位數字，  
   ex:十進位-1265轉換成BCD=> 00000001 00100110 01011101 非常浪費空間。
 * BCD(compressed or packed): 壓縮的BCD碼，四個位元為一單位，1100代表+ 、1101代表-、1111代表無號數字，將正負號放在最後面，  
   ex: 十進位+146 轉換成 packed BCD => 00010100 01101100  
 * [EBCDIC](https://zh.wikipedia.org/wiki/EBCDIC): 像未壓縮的BCD碼，只不過每個Byte 的4個高位元補1，正負號置於最低位元組的4個高位元  
   ex: +146 => 11110001 11110100 11000110  
 * [ASCII](https://zh.wikipedia.org/wiki/ASCII): 像未壓縮的BCD碼，只不過每個Byte 的4個高位元補0011，正負號置於最低位元組的4個高位元  
   ex: +146 => 00110001 00110100 11000110  
 * [Unicode](https://zh.wikipedia.org/wiki/Unicode): 可向下與ASCII兼容，以16位元編碼，因ASCII 不足以容納各國語言而產生
 * [UTF-8](https://zh.wikipedia.org/wiki/UTF-8): 針對Unicode的可變長度字元編碼，由於較小值的編碼點一般使用頻率較高，直接使用Unicode編碼效率低下，大量浪費記憶體空間，UTF-8就是為了解決向下相 容ASCII碼而設計，Unicode中前128個字元，使用與ASCII碼相同的二進位值相同的位元組進行編碼。

<h2 id="0027">data compression</h2> 

* pending

<h2 id="0028">Error detecting and Error correcting</h2> 

* Error detecting Code
  * Parity bit: 利用多加一個bit 的然後把全部的bit XOR起來的方式判定資料是否有錯誤，只能發現一個位元錯誤，並且無法知道錯誤的位置，也無法復原錯誤。  
    以奇核對位元來說: 如果給定一組資料位中1的個數是奇數，補一個bit為0，使得總的1的個數是奇數。例：0000001, 補一個bit為0, 00000010。    
    以偶核對位元來說: 如果一組給定資料位中1的個數是奇數，補一個bit為1，使得總的1的個數是偶數。例：0000001, 補一個bit為1, 00000011。  
  * [checksum](https://medium.com/@a131401203/%E4%B8%AD%E6%96%87%E7%B3%BB%E4%B9%8Bchecksum-808b10b901e1) (之後再補上PCC奇偶校驗)
* Error Correcting Code: 簡稱[ECC](https://zh.wikipedia.org/wiki/%E7%BA%A0%E9%94%99%E5%86%85%E5%AD%98)，通常使用於Memory
  * Hamming distance: 兩組位元組之間有幾個bit不相同，例如10001001 與10110001 有三個地方不一樣，因此Hamming distance為3。
  * Hamming code: [詳解](https://medium.com/@a131401203/%E4%B8%AD%E6%96%87%E7%B3%BB%E4%B9%8Bhamming-code-26ecf5fba50)
<h1 id="003">布林代數與數位邏輯</h1> 

<h2 id="0031">Boolean</h2> 

* 運算子優先順序: NOT > AND > OR
* AND真值表:  
  |輸入(x)| 輸入(y)| 輸出(xy) |
  | --- | --- | --- |
  | 0 | 0 | 0 |
  | 0 | 1 | 0 |
  | 1 | 0 | 0 |
  | 1 | 1 | 1 |
* OR真值表:  
  |輸入(x)| 輸入(y)| 輸出(x+y) |
  | --- | --- | --- |
  | 0 | 0 | 0 |
  | 0 | 1 | 1 |
  | 1 | 0 | 1 |
  | 1 | 1 | 1 |
* NOT真值表:  
  |輸入(x)| 輸出(x')| 
  | --- | --- | 
  | 0 | 1 | 
  | 1 | 0 | 
* 布林恆等式
  | 定律 | AND 形式 | OR形式 |
  | --- | --- | --- |
  | 恆等律 | 1x=x | 0+x=x |
  | 支配律 | 0x=0 | 1+x=1 |
  | 等效 | xx=x | x+x=x |
  | 反轉律 | xx'=0 | x+x'=1 |
  | 交換律 | xy=yx | x+y=y+x |
  | 結合律 | (xy)z=x(yz) | (x+y)+z=x+(y+z) |
  | 分配律 | x+(yz)=(x+y)(x+z) | x(y+z)=xy+xz |
  | 吸收律 | x(x+y)=x | x+xy=x |
  | 笛摩根律 | (xy)'=x'+y' | (x+y)'=x'y' |
  | 雙重取補數 | x''=x | x''=x |

<h2 id="0032">邏輯閘符號</h2> 

* [wiki符號表](https://zh.wikipedia.org/wiki/%E9%82%8F%E8%BC%AF%E9%96%98#%E7%AC%A6%E8%99%9F%E8%A1%A8)

<h2 id="0033">組合邏輯電路</h2> 

* [半加法器](https://zh.wikipedia.org/wiki/%E5%8A%A0%E6%B3%95%E5%99%A8#%E5%8D%8A%E5%8A%A0%E5%99%A8)
* [全加法器](https://zh.wikipedia.org/wiki/%E5%8A%A0%E6%B3%95%E5%99%A8#%E5%85%A8%E5%8A%A0%E5%99%A8):比半加法器多了Cin及Cout，Cin為較低位元進來的值，Cin+A+B為Cout 以及是否進位S。
* [解碼器](https://zh.wikipedia.org/wiki/%E8%AF%91%E7%A0%81%E5%99%A8)
  * 解碼器的其中一個很重要的功能:處理記憶體位置，例如今天有一8晶片記憶體，每晶片8K，總共64K也就是2^16個記憶體位置，需要16個位元來表示，前面三個位元表示第n個晶片，三個位元輸入3線－8線解碼器之後就可以轉換成所需要的晶片，譬如輸出為010代表第2個晶片，以此類推....。
* [多工器](https://zh.wikipedia.org/wiki/%E6%95%B0%E6%8D%AE%E9%80%89%E6%8B%A9%E5%99%A8):輸入的部分會有一組控制線來控制，任何時候只有被選到的輸入可以輸出。
* [產生器/核對器](http://content.saihs.edu.tw/chapter_htm/chapter5/5c/c_06.htm):一個產生parity bit 一個把全部xor 做檢查

<h2 id="0033">序向邏輯電路</h2> 

* 時脈(clock): 
  * 非同步:輸入時及時變動
  * 同步: 以時脈訊號來控制事件
  * 時脈間的間隔時間稱為**時脈週期**
  * 速度通常以gigahertz(GHz)(每秒十億)為單位
  * 所有的序向邏輯電路的記憶元件都以時脈來決定何時更新狀態。

* 正反器(flip-flop):
  * 可以儲存狀態
  * SR正反器: [超詳細解說](https://www.youtube.com/watch?v=KM0DdEaY5sY&list=LL&index=1)
  * ![加上interrupt 之後的cycle](/imgs/20180924000054905.jpg)
    | S  R | Q(t+1)表下一狀態 |
    | --- | --- |
    | 0  0 | Q(t)(狀態不變) |
    | 0  1 | 0(reset) |
    | 1  0 | 1(set) |
    | 1  1 | 未定義(看誰先到) |
  * D 正反器

  <h1 id="004">MARIE</h1> 
  
  * ## [暫存器與匯流排](#0048) #
  * ## [指令的處理](#0049) #

<h2 id="0048">暫存器與匯流排</h2>
 
  * ### 名詞解釋:
  * **暫存器** : CPU 裡面儲存資料的東西。
  * **ALU**: Arithmetic logic unit (算術邏輯單元)，負責運算的工作。
  * **Control Unit** : 控制單元，負責指揮、控制CPU 運作的單元。
  * **PC** : Program Counter(程式計數器)，暫存器的一種，負責存放要執行的指令的位置。
  * **IR** : Instruction Register(指令暫存器)，存放要被執行的指令
  * **MAR** : Memory address register(記憶體位址暫存器)，存放PC 傳過來的位址
  * **MBR(MDR)** : Memory buffer register(Memory data register) 存放從記憶體讀入，或正要寫入記憶體的資料。
  * **AC** : accumulator(累加器)，通用暫存器，存放CPU 要處理的資料 
  * **Flag register** : 旗標暫存器，負責CPU執行指令後的各種狀態，例如運算結果是否為0、計算中是否產生進位以及結果是否等於負值等等。
  * **ISA** : (instruction set architecture)指令集架構。
* <h2 id="0049">指令的處理</h2>  

  * [Machine Cycle](https://medium.com/@a131401203/2a7f1446993c)(又稱von Numann execution cycle 或 instruction cycle) : 擷取->解碼->執行 為一個單位
  * 加上interrupt 之後的cycle![加上interrupt 之後的cycle](/imgs/20180924000054905.jpg)







