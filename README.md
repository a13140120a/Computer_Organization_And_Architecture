# Computer_Organization_And_Architecture

* ## [基礎概念](#001) #
* ## [數據表示法](#002) #
* ## [布林代數與數位邏輯](#003) #
* ## [MARIE](#004) #
* ## [MIPS](#005) #
  
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
    **以奇核對位元來說** : 如果給定一組資料位中1的個數是奇數，補一個bit為0，使得總的1的個數是奇數。例：0000001, 補一個bit為0, 00000010。    
    **以偶核對位元來說** : 如果一組給定資料位中1的個數是奇數，補一個bit為1，使得總的1的個數是偶數。例：0000001, 補一個bit為1, 00000011。  
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

<h2 id="0034">序向邏輯電路</h2> 

* 時脈(clock): 
  * 非同步:輸入時及時變動
  * 同步: 以時脈訊號來控制事件
  * 時脈間的間隔時間稱為**時脈週期**
  * 速度通常以gigahertz(GHz)(每秒十億)為單位
  * 所有的序向邏輯電路的記憶元件都以時脈來決定何時更新狀態。

* 正反器(flip-flop):
  * 可以儲存狀態
  * SR正反器: 可儲存一個位元，[超詳細解說](https://www.youtube.com/watch?v=KM0DdEaY5sY&list=LL&index=1)
  * ![SR](/imgs/SR.png)
    | S  R | Q(t+1)表下一狀態 |
    | --- | --- |
    | 0  0 | Q(t)(狀態不變) |
    | 0  1 | 0(reset) |
    | 1  0 | 1(set) |
    | 1  1 | 未定義(看誰先到) |
  * JK 正反器: 與SR基本上相同，唯一不同處是當輸入均為1時，反轉目前狀態，適合製作Program Counter(PC暫存器)。
  * ![JK](/imgs/JK.png)
  * | J  K | Q(t+1)表下一狀態 |
    | --- | --- |
    | 0  0 | Q(t)(狀態不變) |
    | 0  1 | 0(reset) |
    | 1  0 | 1(set) |
    | 1  1 | 反轉(1變0，0變1) |
  * D 正反器: 最能代表真實的計算機元件(通常是暫存器)，輸入為1且有時脈發生時輸出為1，輸入為0且有時脈發生時輸出為0。
  * ![D](/imgs/D.jpg)  ![JK](/imgs/JK.png)
  * | D | Q(t+1)表下一狀態 |
    | --- | --- |
    | 0 | 0 |
    | 1 | 1 |
    
<h2 id="0035">有限狀態機</h2> 

* Pending

<h1 id="004">簡易計算機架構(MARIE)</h1> 

參考書籍: https://www.amazon.com/Essentials-Computer-Organization-Architecture/dp/1449600069

* MARIE, a Machine Architecture that is Really Intuitive and Easy，書中描述MARIE 是一簡易計算機架構，可讓人輕易的了解計算機大致上的運作方式及結構，其包含以下結構:
  * 16-bit的資料字組
  * 16-bit的指令 4 位元的 opcode 和 12 位元的位址
  * 16-bit算術邏輯單元 (ALU)
  * 16-bit的累加器(AC)
  * 16-bit的IR
  * 16-bit的MBR
  * 12-bit的PC
  * 12-bit的MAR
  * 8-bit的輸入暫存器(InREG)
  * 8-bit的輸出暫存器(OutREG)

* ## [CPU](#0041) #
* ## [匯流排(bus)](#0041) #
* ## [暫存器與匯流排](#0048) #
* ## [指令的處理](#0049) #

<h2 id="0041">CPU</h2>

* 暫存器，CPU內部速度非常快的儲存體，D正反器可以製作暫存器，一個D正反器相當於一個位元的暫存器，某些特定的暫存器只能用來做下述用途，不能用作其他用途。
  * **PC** : Program Counter(程式計數器)，暫存器的一種，負責存放要執行的指令的位置。
  * **IR** : Instruction Register(指令暫存器)，存放要被執行的指令
  * **MAR** : Memory address register(記憶體位址暫存器)，存放PC 傳過來的位址
  * **MBR(MDR)** : Memory buffer register(Memory data register) 存放從記憶體讀入，或正要寫入記憶體的資料。
  * **AC** : accumulator(累加器)，通用暫存器，存放CPU 要處理的資料 
  * **Flag register** : 旗標暫存器，負責CPU執行指令後的各種狀態，例如運算結果是否為0、計算中是否產生進位以及結果是否等於負值等等。
  * **InREG** : 輸入暫存器，存放由設備傳來的數據
  * **OutREG** : 輸出暫存器，存放要輸出給設備的數據

* **ALU**: Arithmetic logic unit (算術邏輯單元)，CPU內負責運算工作的單位。
* **Control Unit** : 控制單元，負責指揮、控制CPU 運作的單元。


<h2 id="0042">匯流排(bus)</h2>

* 匯流排週期: CPU通過匯流排和存儲器或I/O接口進行一次數據傳輸所需要的時間
* 用來連結系統中多個子系統共用且通用的數據傳輸通道的一組導線。
* 含有多條線，可以多個位元同時傳輸。
* 任何時刻僅有一個裝置可以使用匯流排
* 速度受其長度及共用他的裝置的數量影響
* 常被區分為**主動(master)** 與 **被動(slave)** ，主動式發起動作者，被動是回應動作者。
* 可以是點**對點(point to point)**，或者是 **共用的(common pathway)(又稱為multipoint)**
* 一組匯流排又可以包含:
  * 數據線(data bus 又稱數據匯流排): 用來傳輸資料。
  * 控制線(control lines): 控制哪個裝置被允許使用，以及目的為何，也必須要用來回覆使用的請求(request)、打斷(interrupt)、以及時脈傳送過來的訊號。
  * 位址線: 資料應被讀出或寫入的位址。
  * 電源線: 顧名思義。
* 匯流排依據傳送不同類型的資訊又可分為以下:
  * processor-memory buses(處理器-記憶體匯流排): 短而高速，力求盡可能地提高頻寬。
  * I/O busses(IO 匯流排): 較processor-memory buses 長，可配合各種不同頻寬的設備。
  * backplane buses(背板匯流排)，做在機器底板上來連接處理器、IO、及Memory，許多電腦會有階層式匯流排，高效能系統通常會使用所有的三種匯流排。
* PC上的匯流排亦有屬於自己的專用術語:
  * system bus(系統匯流排): 連結cpu、memory 以及其他所有內部組件。
  * expansion buses(延伸匯流排): 連接外部裝置、周邊設備、擴充槽與部分的IO Port，速度較慢。
  * local buses(區域匯流排): 是那些連接周邊裝置到cpu 的匯流排，只能用於連接數量有限的類似裝置，速度非常快。
* 匯流排又可分為同步與非同步:
  * 同步匯流排: 只有在時脈變動時發生，會因為匯流排長度而導致時脈偏斜(clock skew)，匯流排週期不可以短於資訊在匯流排上傳遞所需的時間，因此匯流排的長度會對匯流排的時脈速率以及匯流排時間造成限制。
  * 非同步匯流排: 控制訊號協調，並且需要使用handshaking protocal(握手協定)來保持時序，以下是從記憶體讀出資料的流程:
    1. ReqREAD: 這條控制線被致動，資料的記憶體被放到匯流排線上
    2. ReadyDATA: 這條控制線在記憶體系統已經把所需要的資料放上匯流排時被設定
    3. ACK: 這條控制線是對方用於表示已經收到 ReqREAD或ReadyDATA。
* 匯流排使用時必須先預約，在多於一個主動裝置的系統中需要做bus arbitration(匯流排仲裁)，方法可分以下四大類:
  * Daisy Chain Topology（菊花鏈拓撲）: 使用一條從最高優先權裝置像最低優先權裝置傳遞下去的「同意授予匯流排」控制線，此方法不具公平性，最低優先權有可能餓死。
  * centralized parallel arbitration: 美個裝置在匯流排中會有一條請求控制線，會有一個集中式的仲裁器選擇誰可以使用匯流排，此方法可能會有瓶頸。
  * distributed arbitration using self-selection: 這方法與centralized parallel arbitration 類似，但是並非由集中式的仲裁器選擇誰可以使用匯流排，而是各自投票決定誰有最高優先權。
  * distributed arbitration using collision detection: 每個裝置都可以發出請求，若發生碰撞則重新送出請求。


<h2 id="0043">ISA(instruction set architecture)指令集架構</h2>

* MARIE的instruction 長度均為16 bit，且前四個位元為**opcode**(運作碼)，其他的12個位元為記憶體位址(代表支援2^12個記憶體位置)
* 分為直接定址(direct address) 與間接定址(indirect address):
  * direct address: x欄位中的值為真正地址
  * indirect address: x 欄位中的值指向另一個記憶體位置
* 一個把記憶體位置0000 0000 0011 Load 進AC暫存器的指令如下:
* ![一個把記憶體位置0000 0000 0011 Load 進AC暫存器的指令](/imgs/opcode2.png)
  | 二進位 | 指令 | 意義 |
  | --- | --- | --- |
  | 0001 | Load x | 將記憶體位址x的內容載入AC |
  | 0010 | Store x | 將AC的內容儲存至記憶體位址x |
  | 0011 | Add x | 將位址X內容加至AC中，並將結果儲存於AC |
  | 0100 | Sub x | 將AC內容減去位址X內容，並將結果儲存於AC |
  | 0101 | Input x | 將IO裝置的值儲存於AC中 |
  | 0110 | Output x | 將AC的內容輸出於IO裝置 |
  | 0111 | Halt | 結束程式 |
  | 1000 | Skipcond | 根據條件跳過下一道指令 |
  | 1001 | Jump x | 將x的值載入PC |
  | 0000 | JnS X | 將PC的值儲存於X，並跳至X+1 |
  | 1010 | Clear | AC全部設為0 |
  | 1011 | AddI X | 記憶體位置X的內容為另一個記憶體位置Y，將記憶體位址Y的內容與AC相加 |
  | 1100 | JumpI X | 記憶體位置X的內容為另一個記憶體位置Y，將Y的值載入PC |
  | 1101 | LoadI X | 記憶體位置X的內容為另一個記憶體位置Y，將記憶體位址Y的內容載入AC |
  | 1110 | StoreI X | 記憶體位置X的內容為另一個記憶體位置Y，將AC的內容儲存至記憶體位址Y |

* 指令集又分CISC(複雜指令集)及RISC(精簡指令集):
  * CISC: 有很多指令，長度不固定，格式複雜，缺點是某些較複雜的指令會大量拖累速度。Intel 的x86系列都是CISC。
  * RISC: 主要目的為簡化指令，使其速度更快，每到指令只執行一個動作，指令長度都一樣，格式簡單。Pentium跟MIPS 都是RISC

* microoperation(微運作): 每道instruction 都是由數個microoperation所構成的，例如Load 時，需先將memory address 載入MAR，Fetch 之後將資料儲存於MBR，再將MBR的內容載入AC
* RTN(register transfer notation): 暫存器傳遞表示法，又稱RTL(register transfer language)，M[x]表示儲存於記憶體位置x中的數據，<- 表示資訊的傳遞。
* 指令詳解(實際上的microoperation其實會受到匯流排設計的影響而有所不同):
  * Load X: 將記憶體位址X 置於MAR，然後將M[MAR] 處(或位址X)的資料複製入MBR，然後將資料儲存於AC中:
  ```
  MAR <- X
  MBR <- M[MAR]
  AC <- MBR
  ```
  *  Store X:
  ```
  MAR <- X, MBR <- AC  (因為書中兩個暫存器間有匯流排連結，所以可以僅用一個時脈就完成)
  M[MAR] <- MBR
  ```
  *  Add X:
  ```
  MAR <- X
  MBR <- M[MAR]
  AC <- AC + MBR
  ```
  *  Sub X:
  ```
  MAR <- X
  MBR <- M[MAR]
  AC <- AC - MBR
  ```
  *  Input: 從IO設備傳過來的資料會先被放在InREG中
  ```
  AC <- InREG
  ```
  *  Output: 資料要輸出到IO 設備之前需要先放到OutREG 裡面
  ```
  OutREG <- AC
  ```
  *  Halt: 單純停止一個程式
  *  Skipcond: 這個指令會依照第10 及11個位元(opcode 旁邊的兩個位元)，來決定AC對什麼做比較 => 1000[11]0000000000裡面中括號的兩個位元
  ```
  If IR[11~10] = 00 then (如果IR中位元10與11均為0)
      If AC < 0 then PC <- PC+1 (若AC為負則略過下一道指令)
  If IR[11~10] = 01 then (如果IR中位元10與11為01)
      If AC = 0 then PC <- PC+1 (若AC為0則略過下一道指令)
  If IR[11~10] = 10 then (如果IR中位元10與11為10)
      If AC > 0 then PC <- PC+1 (若AC大於0則略過下一道指令)
  若兩個位元均為1，則發生錯誤。
  ```
  *  Jump X: 無條件跳轉到X的位置
  ```
  PC <- X
  也可寫成:
  PC <- IR[11~0]
  ```
  * JnS: 
  ```
  # 將PC的值存到記憶體位置X
  MBR<-PC
  MAR<-X
  M[MAR]<-MBR
  跳轉到X+1
  MBR<-X
  AC<-1
  AC<-AC+MBR
  PC<-AC
  ```
  * Clear:
  ```
  AC<-0
  ```
  * AddI X:
  ```
  # 取記憶體位置X的值
  MAR<-X
  MBR<-M[MAR]
  #以記憶體位置X的值當成另一個記憶體位置然後取值
  MAR<-MBR
  MBR<-M[MAR]
  # 相加
  AC<-AC+MBR
  ```
  * JumpI X:
  ```
  # 取X的值
  MAR<-X
  MBR<-M[MAR]
  # Jump到X的值的位置
  PC<-MBR
  ```
  LoadI X:
  ```
  # 取記憶體位置X的值
  MAR<-X
  MBR<-M[MAR]
  #以記憶體位置X的值當成另一個記憶體位置然後取值
  MAR<-MBR
  MBR<-M[MAR]
  # 將結果存於AC
  AC<-MBR
  ```
  StoreI X:
  ```
  # 取記憶體位置X的值
  MAR<-X
  MBR<-M[MAR]
  # 只有MAR能Fetch, 所以放進MAR
  MAR<-MBR
  # 儲存資料
  MBR<-AC
  M[MAR]<-MBR
  ```
  
  
* <h2 id="0044">指令的處理</h2>  
  * [Machine Cycle](https://medium.com/@a131401203/2a7f1446993c)(又稱von Numann execution cycle 或 instruction cycle) : 擷取->解碼->執行 為一個單位
  * 加上interrupt 之後的cycle![加上interrupt 之後的cycle](/imgs/20180924000054905.jpg)
  * (Interrupt:pending)[123]  
  
* 以下為MARIE一簡易程式:
  | 16進位位址 | 指令 | 記憶體中內容(二進制) | 記憶體中內容(16進制) |
  | --- | --- | --- | --- |
  | 100 | Load 104 | 0001000100000100 | 1104 |
  | 101 | Add 105 | 0011000100000101 | 3105 |
  | 102 | Store 106 | 0010000100000110 | 2106 |
  | 103 | Halt | 01110000000000000 | 7000 |
  | 104 | 0023 | 0000000000100011 | 0023 |
  | 105 | FFE9 | 1111111111101001 | FFE9 |
  | 106 | 0000 | 0000000000000000 | 0000 |
  
* 其各暫存器的值與對應的RTN:

  Load 104:   
  | 步驟 | RTN | PC | IR | MAR | MBR | AC |
  | --- | --- | --- | --- | --- | --- | --- |
  | 初始值 |  | 100 | --- | --- | --- | --- |
  | 擷取 | MAR<-PC | 100 | --- | 100 | --- | --- |
  |  | IR<-M[MAR] | 100 | 1104 | 100 | --- | --- |
  |  | PC<-PC+1 | 101 | 1104 | 100 | --- |---  |
  | 解碼 | MAR<-IR[11~0] | 101 | 1104 | 104 | --- | --- |
  |  | MBR<-M[MAR] | 101 | 1104 | 104 | 0023 | --- |
  | 執行 | AC<-MBR | 101 | 1104 | 104 | 0023 | --- |
  
  Add 105:
  | 步驟 | RTN | PC | IR | MAR | MBR | AC |
  | --- | --- | --- | --- | --- | --- | --- |
  | 初始值 |  | 101 | 1104 | 104 | 0023 | 0023 |
  | 擷取 | MAR<-PC | 101 | 1104 | 101 | 0023 | 0023 |
  |  | IR<-M[MAR] | 101 | 3105 | 101 | 0023 | 0023 |
  |  | PC<-PC+1 | 102 |3105 | 101 | 0023 | 0023 |
  | 解碼 | MAR<-IR[11~0] | 102 | 3105 | 105 | 0023 | 0023 |
  |  | MBR<-M[MAR] | 102 | 3105 | 105 | FFE9 | 0023 |
  | 執行 | AC<-MBR | 102 | 3105 | 105 | FFE9 | 000C |
  
  Store 106:
  | 步驟 | RTN | PC | IR | MAR | MBR | AC |
  | --- | --- | --- | --- | --- | --- | --- |
  | 初始值 |  | 102 | 3105 | 105 | FFE9 | 000C |
  | 擷取 | MAR<-PC | 102 | 3105 | 102 | FFE9 | 000C |
  |  | IR<-M[MAR] | 102 | 2106 | 102 | FFE9 | 000C |
  |  | PC<-PC+1 | 103 | 2106 | 102 | FFE9 | 000C |
  | 解碼 | MAR<-IR[11~0] | 103 | 2106 | 106 | FFE9 | 000C |  |
  | 執行 | MBR<-AC | 102 | 2106 | 106 | 000C | 000C |
  |  | M[MAR]<-MBR | 103 | 2106 | 106 | 000C | 000C |


<h2 id="0045">組譯器</h2>
  
* 組譯器的工作是將組合語言(助憶碼)轉換成機器碼(machine code)。
* 組譯器讀入來源檔(source file)並產出目的檔(object file)。
* 可用label(標籤) 來當成記憶體位置，以利組合語言撰寫，缺點是會加重組譯器工作。
* 組譯器至少必須要從頭到尾掃描兩次程式碼，第一次建立symbol table(符號表)來連結label與記憶體位置，第二次轉譯時，組譯器就可根據符號表取得對應的machine code。
* 以迴圈將5個數字相加的簡易編程:
  ```
  十六進位地址    label       指令
  100                        Load     Addr  / 將117 load到AC中
  101                        Store    Next  / 將117 store到Next中
  102                        Load     Num   / 將5 load到AC中
  103                        Sub      One   / AC的值減1，此時AC值為4
  104                        Store    Ctr   / 將 4 store到Ctr，此時Ctr為4
  105            Loop,       Load     Sum   / 將總和 load到AC中
  106                        AddI     Next  / 以Next的值(117,118....)為記憶體位置，與AC相加
  107                        Store    Sum   / 然後存回去
  108                        Load     Next  / 把下一個指標load近來
  109                        Add      one   / 指向下一個位置
  10A                        Store    Next  / 存回去
  10B                        Load     Ctr   / 把目前迴圈數i load到AC中
  10C                        Sub      One   / 減1
  10D                        Store    Ctr   / 存回去
  10E                        Skipcond 000   / 判斷是否為0，若是則跳過下一行結束，
  10F                        Jump     Loop  / 若否，則回到Loop
  110                        Halt           / 結束
  111            Addr,       Hex      117   / 第一個數字的記憶體位置
  112            Next,       Hex      0     / 下一個數字的指標
  113            Num,        Dec      5     / 迴圈總數
  114            Sum,        Dec      0     / 存放和的地方
  115            Ctr,        Hex      0     / 控制迴圈的i
  116            One,        Dec      1     / 用於遞增或遞減
  117                        Dec      10    / 從這裡開始以下為要被加總的五個數字
  118                        Dec      15
  119                        Dec      20
  11A                        Dec      25
  11B                        Dec      30
  ```

<h2 id="0046">解碼</h2>

* 解碼其實就是利用許多邏輯閘來控制資料流向，通常一個microoperation會對應到一組控制訊號
* 又分為**硬連線控制** 與**微程式控制**
  * 硬連線控制:將IR中的指令透過基本的邏輯閘轉換為控制訊號   
      速度較快，但是體積較大，而且無法設計太複雜的指令集，硬連線控制具備三個元件:指令解碼器、週期計數器、控制矩陣
  * 微程式控制:使用microcode產生控制訊號，將IR裡面的指令輸入到 microprogram(通常是燒在ROM、PROM、EEPROM裡面的解譯器)裡面，然後產生控制訊號
      速度較慢，但較靈活，修改指令集只需修改microprogram即可，不用修改電路，且可以設計許多複雜的指令集，目前於個人電腦上位居主流。


<h2 id="0047">Intel</h2>

* 8086 的四個重要的16位元暫存器，分別為AX(accumulator)、BX(擴充定址能力)、CX(計數器)、DX(數據暫存器)，每個暫存器依據高位元處與低位元處又可分為AH、BH、CH、DH、AL、BL、CL、DL，其他還有用於表示stack 位移量的指標SP、stack 基底指標(BP)、還有Prpgram Counter(IP)、
* 8086 的組合語言分成不同的segments，code segment存放程式碼，data segment 存放數據，還有stack segment存放stack，要從任何segment存取資料都必須指定從segment的開頭到位移處，因此就有了存放segment 的暫存器，CS存放code segment，DS存放data segment，SS存放stack segment，還有額外區段的SS暫存器，位址使用xxx:yyy的形式定義，其中xxx為區段暫存器中的值，yyy為偏移量。
* 80386出現時，為了向下相容，對原本的16位元暫存器擴增成32位元，將AX、BX、CX、DX又增加了EAX(Extend AX)、EBX、ECX、EDX，並保留原本的暫存器。
* 指令集採用[little endian](#0052)，裡個位址，並且是[GPR 裡面的register-memory](#0053) 架構。


<h2 id="005">Instructionse</h2>

<h2 id="0051">格式</h2>

* 可依下列特性作為區分:
  * 運算元的儲存方式:以stack的方式 或者暫存器中
  * 運算元數量
  * 運算元的位置:記憶體或者暫存器
  * 運作:例如那些可以存取記憶體，哪些不行
  * 運算元的型態:是地址，還是數字

* 設計Instructionse時需以下列因素做為考量:
  * 程式可使用的空間
  * 指令集的複雜度
  * 指令的長度
  * 指令的總數

* 短指令通常占用較少空間，且速度較快，缺點是可用數量少、運算元數量也較少。
* 固定長度的指令解碼較快，但較浪費空間
* 記憶體的組織與指令有很大的關聯，例如若記憶體使用16或32個bit而不已byte定址的話，則難以存取單一字元符號。
* 固定長度的指令集並不一定要固定數量的運算元。
* 存在許多種定址模式
* 位元組存放順序:大小端

<h2 id="0052">big endian/little endian</h2>

* [big endian](https://zh.wikipedia.org/wiki/%E5%AD%97%E8%8A%82%E5%BA%8F#%E5%A4%A7%E7%AB%AF%E5%BA%8F): 閱讀較為容易，可以立刻從位移值0來判斷正負，於串列上運作時速度較快，大部分圖片檔都是以big endian方式擺放，缺點是將32位元轉換成16位元時較麻煩，不允許以非word的方式儲存(例如word是2個bytes 時不能從第1個byte 的位置放起)，編程較不易。
* [little endian](https://zh.wikipedia.org/wiki/%E5%AD%97%E8%8A%82%E5%BA%8F#%E5%B0%8F%E7%AB%AF%E5%BA%8F): 計算高精確度算數時較容易，允許非word的方式儲存，編程容易，計算機網路通常採用little endian方式。

<h2 id="0053">種類</h2>

* stack architectures:EX
  ```
  Push X
  Pop  Y
  Mult
  Add
  ```
* accumulator architecture(只有一個暫存器):EX
  ```
  Add X
  ```
* general-purpose register(GPR):又可分成三種
  * memory-memory: 允許不使用暫存器的情況下運作
  * register-memory: 至少要包含一個暫存器
  * load-store: 只能有暫存器，所有牽涉到記憶體的數據都必須先載入暫存器

<h2 id="0054">Expanding opcode</h2>

* Expanding opcode 代表的是一套豐富的opcode，但又希望opcode能夠很短的折衷作法，利用escape opcode來達成
* 例如育編碼以下所有指令:
  * 15道具有三個位址的指令
  * 14道具有兩個位址的指令
  * 31道具有一個位址的指令
  * 16道具有0個位址的指令
```
# 15道具有三個位址的指令
0000 R1 R2 R3
....
1110 R1 R2 R3
1111  # escape opcode

# 14道具有兩個位址的指令
1111 0000 R1 R2
...
1111 1110 # escape opcode

# 31道具有一個位址的指令
1111 1110 0000 R1
...
1111 1111 1111 # escape opcode
```
* 當前四個位元為1111時，代表此道指令有兩個或一個位址
* 當前八個位元為1111 1110時，代表此道指令有一個位址
* 當前面12個位元為1111 1111 1111時，代表此opcode 沒有位址

* 如果要用12個位元設計指令集，3個位元用來表示暫存器，且不允許直接存取記憶體，並且想創造出:
  * 4道具有三個位址的指令
  * 255道具有一個位址的指令
  * 16道具有0個位址的指令
  * 前四道指令需4 * 2^3 * 2^3 * 2^3 = 2048種bit pattern，接著255道指令需255 * 2^3 = 2040，加上最後16道指令總共4104種，然而12位元只能有4096種bit pattern，所以無法達成目標。

<h2 id="0055">定址</h2>

* immediate addressing: 例如Load 008，cpu 會直接把008載入AC中
* direct addressing: 例如Load 008，cpu 會把記憶體位址008的值載入AC中
* indirect addressing: 例如Load 008，cpu 會直接把記憶體位址008的值當成address y，然後去y找資料
* register addressing: 會將暫存器中的值載入
* register indirect addressing: 會將暫存器中的值當成位址，然後載入位址的資料。


<h2 id="005">MIPS</h2>
  
<h2 id="0051">介紹</h2>
  
* 參考資料: [清大黃婷婷教授](https://youtube.com/playlist?list=PLS0SUwlYe8czszh6M74JCU0mIUL_ymBbe)  
* ISA 屬於RISC，Load-Store architecture，只能以暫存器作為運算元，
* MIPS32 裡面因為memory 的地址太大無法塞進instruction 所以address 都存在register 裡面
* 分為三種型態:
  * R-format: for register:
    * 6bit opcode,5bit source register, 5bit target register(注意跟組語不同), 5bit destination register, 5bit shift amount, 6bit function
    * opcode 用來表示哪種type, fumction 用來表示例如add, sub等等
    * shift amount 為5個bit 剛好可以shift 32個bit，再多就無意義了，有些指令例如add 此field為0。
  
  * i-format: for immediate、lw and sw
    * 6bit opcode,5bit source register, 5bit target register, 16bit immediate
    * immediate 會被extend 成32bit 的有號數(負的會全補1，正的會全補1)，若是lw或sw，則此field會是offset的值
  * J-foramt: for jump: 分成 condotional 跟 unconditional
    * condotional 有beq(branch equal), bnq(branch not equal)
    * unconditional 則是 j(jump)
* 暫存器種類:
  * 0:zero constant，因為運算很常用到0，包括mov的動作或者not，所以就直接有了一個0暫存器增加速度
  * v0: results  (return value)
  * v1: expression (return value)
  * a0~a3: arguments
  * t0~t7: temporary, caller saves
  * s0~s7: callee saves (local variable)
  * t8~t9: more temporary saves
  * k0、k1: for os kernel
  * gp: pointer to global area
  * sp: stack pointer
  * fp: frame pointer
  * ra: return address (跳轉前儲存現在的位址的暫存器)


<h2 id="0052">基本語法</h2>

* 把記憶體位置1012的值載入暫存器t0:
```
$s0=1000
lw $t0, 12($s0)  # load word
```
* store t0(=25) 到記憶體位置1012
```
$s0=1000
$t0=25
sw $t0, 12($s0)  # store word
```
* C code : `g = h+ A[8]`，其中$s1=g, $s2=h, $s3=A的base address
```
lw $t0, 32($s3)  # 因為一個word 為4個byte
add $s1, $s2, $t0
```
* 常數指令:
```
#s1+10放到s0裡面
addi $s0, $s1, 10
```
* 第0個register always=0
```
# 不會有任何事發生
add $zero, $zero, 10
```
* MIPS 沒有mov所以用add zero暫存器:
```
#s0 mov 到 t0
add $t0, $s0, $zero
```
* sll:shift left(補零), srl: shift right(補零),sra: shift right but fill empty by singed(負補1，正補0)   
* and: 將bit pattern 做and
```
and $t0, $t1, $t2
```  
* MIPS 沒有NOT，使用NOR(A NOR B=NOT(A OR B) )，所以先NOR 0就等於NOT
```
nor $t0, $t1, $zero
# t1 = 00011
# t0 = 11100
```
* bne and j:
```
# in C:
if (i==j) f=g+h;
else f=g-h;

# in MIPS
        bne $s3, $s4, Else  # i!=j則跳到Else，等於則下一行
        add $s0, $s1, $s2
        j Exit              # jump 到Exit
Else:   sub $s0, $s1, $s2
Exit:
```
* Signed:
  * slt rd, rs, rt : if (rs<rt) rd=1;else rd=0 # 設定旗標
  * slti rt, rs, constant : if (rs < constant) rt=1;else rt=0
  ```
  slt $t1, $s0, $s1
  bne $t0, $zero, Less
  ```
* Unsigned: sltu, sltui:

<h2 id="0053">Procedure Call</h2>
  

  
  
  
  

