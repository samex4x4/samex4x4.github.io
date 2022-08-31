---
title: DDIA-ch9-Consistency-and-Consensus
date: 2021-07-06 21:05:59
tags:
    - 讀書心得
---

# Consistency and Consensus: 一致性與共識

承上回，分布是系統很有可能出錯，因此需要找出容錯的方法，即使某些內部組件出現故障也能正常運行。

以下將假設一些第8章的問題會發生:
- 數據丟失
- 順序不一致
- 重複資料
- 數據延遲
- 節點崩潰

建構容錯系統的最好方法，是找到一些通用的且具有可用保證的抽象，實現一次後讓應用依賴這些保證上。這和第7章的事務處理方法相同，透過事務，應用假裝沒有崩潰(原子性)，沒有其他人同時使用資料庫(隔離性)，儲存設備是完全可靠的(持久性)。即使真的崩潰了，事務抽象隱藏了這些問題，因此應用不用擔心。

因此重點是尋求可以讓應用忽略分布式系統的抽象，例如分布式系統最重要的抽象之一就是共識(Consensus): **讓所有節點對某件事情達成一致**。一旦有共識，應用可以其用在各種層面。ex有一個單一主節點複製的資料庫，如果主資料庫掛掉，需要切換到另一個節點，剩餘的節點可以用共識來推舉新的領導者，正如第5章處理節點當機中所討論的那樣，重要的是只有一個領導者，且所有的節點都認同。如果有兩個節點都認為自己是領導者，這種情況稱為腦裂(split brain)，會造成數據丟失。

因此需要先列出在分散式系統中提供的保證和抽象的範圍，怎樣是可以／不可以的範圍？在某些情況下系統可以容忍錯誤，有些則完全不行，需要確認哪些是基本限制。

## 一致性保證

在複製延遲問題中，會看到數據庫複製中發生的時序問題，如果在同一時刻查看兩個不同的資料庫節點。則可能看到不同的數據，因為寫入請求在不同的時間到達不同的節點。無論使用哪種複製(單一主節點、多節點複製或是無主節點複製)都會出現不一致的狀況。

大多數複製的資料庫至少提供了**最終一致性**，不一致是暫時的，最終會自行解決(假設網路中的故障被修復的話)，最終一致性的另一個更好的名字可能是收斂(convergence)，因為預期所有的副本最終被收斂到相同的值。

對開發人員而言，最終一致性是很難的，因為和普通單線程程序中便量有很大的區別。後者修改變量後再次讀取，不可能讀到舊值，或者讀取失敗。資料庫表面上看起來像是可以讀寫的變量，但實際上更加複雜。在使用只提供弱保證的資料庫時要意識到侷限性，而不是做出太多假設。錯誤往往是很難找到、也很難被測試到的，因為大多數情況下會運行良好。當系統出問題或是高併發時，最終一致性的邊緣情況才會顯現出來。

本章將討論更強一致性的模型，然而具有更強保證的系統可能比保證較差的系統具有更差的效能或更少的容錯性。儘管如此它們更容易被正確使用，彼此比較後才能更好決定哪些更符合自己的需求。