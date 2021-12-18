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



<h2 id="0021">基礎概念</h2> 

* bit(位元): 電腦中最基本的單位，是電路中的開(高電位) 或關(低電位)的狀態
* byte(位元組): 8個bits
* word(字組): 表示特定環境下處理起來最有效率的單位，大小不一定是幾個bit，看環境決定。
* overflow(溢位): 超過指定bit 能夠表示的範圍，例如8個bit的無號整數可表示0-255，當值等於256的時候發生溢位。  
  又或者想要把長度為4bits 的兩個二進位數相加:1111+1111，這種情況下就會發生溢位。 

<h2 id="0022">有號整數表示法</h2> 

* Unsigned Representation(無號數表示法): Unsigned就是沒有符號的意思，因為沒有符號，所以不會有負數。
* 而Signed就是有符號的意思，所以會有分負數與正數，Singed Representation 較常見的又分為以下幾種
  * sign-magnitude representation: 顧名思義就是 符號-大小 的表示法，第一個bit控制正負，其他的bit表示大小。  
    => 最基礎的負數表達方法，電路設計困難，有兩個0的表示法。
  * 1's Complement: 1轉0，0轉1，溢位要再 + 1。  
    => 好處是設計電路簡單，缺點有兩個0的表示法
  * 2's Complement: 1's Complement + 1。
    => 設計電路簡單，改善有兩個0的表示法問題，缺點是能表示的正負範圍不對稱，ex: 4bit = -8~7
  * Excess: 偏移值2的n-1次方-1為中心點0做計算。





<h1 id="003">布林代數與數位邏輯</h1> 









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







