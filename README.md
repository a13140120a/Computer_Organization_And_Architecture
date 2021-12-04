# Computer_Organization_And_Architecture

* ## [緒論](#001) #
  * ## [概論](#0011) #
    
    
  <h1 id="001">緒論</h1> 
  
* <h2 id="0011">概論</h2>  

    * 計算機組織(computer organization):
      * 物理相關面向，探討控制訊號、訊號傳遞方式與記憶體型態等議題。
    * 計算機結構(computer architecture):
      * 邏輯抽象層面，注重計算機的架構與行為，內容包含指令集與格式、運作碼、數據型態暫存器數量與型態、定址模式、主記憶體存取方法與各種I/O機制等元素。 
    * ### 計算機主要元件:  
      1.  cpu   
      2.  memory  
      3.  I/O device  
    * ### 容量單位:  
      字首大寫表示2的次方(K, M G)，小寫表示10的次方，大寫B代表Byte，小寫b代表bit,
      |符號| 說明 |
      |--- | --- |
      |K| 1KB = 1 * 2^10 Bytes, 1Kb = 1 * 2^10 bits|
      |M| 1MB = 1 * 2^20 Bytes, 1Mb = 1 * 2^20 bits|
      |G| 1GB = 1 * 2^30 Bytes, 1Gb = 1 * 2^30 bits|
      |k| 1kB = 1 * 10^3 Bytes, 1Kb = 1 * 10^3 bits|
      |m| 1mB = 1 * 10^6 Bytes, 1mb = 1 * 10^6 bits|
      |g| 1gB = 1 * 10^9 Bytes, 1gb = 1 * 10^9 bits|
      
    * ### 摩爾定律(Moore's law):
      積體電路上可容納的電晶體數目，約每隔兩年便會增加一倍  [(wiki)](https://zh.wikipedia.org/wiki/%E6%91%A9%E5%B0%94%E5%AE%9A%E5%BE%8B)
      
    * ### 計算機階層:  
      |level | 說明 | e.g. |
      |--- | --- | --- |
      |6| User | 程式 |
      |5| 高階語言 | C++、Java etc. |
      |4| 組合語言 | 組合語言 |
      |3| 系統軟體 | OS、程式庫 |
      |2| 機器 | 指令集(ISA) |
      |1| 控制 | microcode、hardwired |
      |0| 數位邏輯 | 電路、閘(Gate) |
    * ### 雲服務:  
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

    * ### 馮紐曼(von Neumann):  
      * [見wiki](https://zh.wikipedia.org/wiki/%E5%86%AF%C2%B7%E8%AF%BA%E4%BC%8A%E6%9B%BC%E7%BB%93%E6%9E%84)
      * [history](https://pansci.asia/archives/194219)
      * 馮紐曼週期(von Numann execution cycle): [見4.9](#0049)
    * 












  <h1 id="004">MARIE</h1> 

* <h2 id="0049">指令的處理</h2>  









