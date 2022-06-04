---
title: 如何準備2022 Google Cloud Professional Data Engineer Certification
date: 2022-06-04 17:02:28
tags:
    - 考試
    - Google Cloud 
---

# 介紹

![證照圖](https://i.imgur.com/46DSvvn.png)

近期因應工作內容的變動，有感自己對於平常在使用的Google Cloud Platform(GCP)認識不夠深，想說不如報名考試看看自己的熟悉程度(兼逼迫自己學習)，很幸運的一次就通過了，在這裡紀錄一下我認為該場考試要注意的項目以及我是如何準備的。


# 背景 
資料工程師(5y)，之前接觸過的GCP產品主要是Bigquery, Dataflow, Pub/Sub, Cloud Function等工具，最近在熟悉K8S。
去年有上完Coursera的[課程](https://www.coursera.org/professional-certificates/gcp-data-engineering)，不過過了一年差不多都忘光了(′．ω．`) 

這門課對Data Engineer常使用的GCP產品會介紹基礎知識的和應用場景，最後會有應考對策 & 重點，之前完全沒碰過GCP的人不妨試試看，且有不少練習是可以直接操作上述的產品而不需要額外付費的。 

![Coursera](https://i.imgur.com/yeGFaQD.png)

本次考試我抓一個月左右準備，大多是下班時間看考題以及閱讀文件(約1~2小時)。

# 考試流程

## 註冊

考試註冊[網站](https://cloud.google.com/certification/data-engineer)
會進入，點選註冊後會導向到webssessor，註冊完成後就可以選擇要進行什麼考試了。
![webassessor](https://i.imgur.com/lnBzopl.png)

要注意考試會分成去考場以及遠端的，這次避免自己網路異常還是選擇了考場，台北的考場只有Systex_Taipei(恆逸教育訓練中心)，
另外雖然考試費用寫USD200，但我最後在購物車只有看到USD120，這點是比較疑惑的地方...。 

![testselect](https://i.imgur.com/zWomxux.png)

## 考試情況
 
需提早15分鐘前報到，考試前會將你的包包收走，身上所有東西都要清空，現場還要我把褲管捲起來確認沒有小抄。 

之後會帶你到一個單獨的房間進行考試，會有可以塗寫的板子讓你在考試過程中可以做點筆記。考試有50題，要在兩個小時內完成，完成後按Submit當下就會知道結果，分成兩種結果Pass/Fail，實際上考了幾分一周後會寄email過來，另外到底錯那些題是不知道的。

考完可以收到一個連結可以去挑選小禮物。
![gift](https://i.imgur.com/Tt6MGx1.png)


# 準備方法

先閱讀網路上其他人的心得 -> 閱讀官方文件(第一周) ->　寫考題+根據考題中討論的文件再次閱讀(第二~四周)

因為時間不太夠，第一周的時候我試著把我覺得比較重要的文件都看了一點(ex Bigtable的schema設計、Bigquery計價等等)，但文件真的頗多...，所以後來改採用直接讀網路上的考古題，邊讀邊記錄那些是常考的。就算無法讀完官方文件，也至少要把Best Practice給讀完，因為考題很多是聚焦在這些案例的實作中。
推薦閱讀這本: [Google Cloud Data Engineer Data Dossier](https://lucid.app/lucidchart/0ca44a63-4ea4-4d78-8367-2465512d21be/view?page=vf_Fs9CbV-a6#)，儘管有些東西現在有點過時，但該工具的設計場景以及原則卻是不變的，可以大致上知道這場考試會考那些功能。

## Google 相關服務

在此也整理一下列出來會考的幾個服務，考題重要性依照我寫模擬試題 & 考試當天的印象；

| 工具 | 考題重要性 | 備註 |
|------|--------|------|
|   Bigquery   |   ⭐⭐⭐⭐     |  最常考的工具，必讀，包含語法/schema設計/如何與其他工具整合等等   |
|    Dataflow  |   ⭐⭐⭐     |   時常與 Pub/Sub 搭配，常見於streaming data，建議熟背各 [Windows](https://cloud.google.com/dataflow/docs/concepts/streaming-pipelines) 的特性|
|   Pub/Sub   |   ⭐⭐⭐     |  時常與 Dataflow 搭配，常見於streaming data，熟記Pull/Push的差異    |
|   Cloud SQL   |   ⭐⭐     |  資料庫，會有跟Spanner的比較    |
|   Cloud Spanner   |  ⭐⭐⭐      | 資料庫+cluster，建議熟讀schema設計   |
|   Dataproc   |    ⭐⭐⭐    |   Hadoop生態系，常見從本地端遷移的問題  |
|   Bigtable   |   ⭐⭐⭐     |  IoT常見工具，應對大量資料寫入，建議熟讀schema設計    |
|   DataStore/FireStore   |   ⭐⭐     |  NoSQL 工具，類似MongoDB    |
|   Machine Learning   |     ⭐⭐⭐   |  無關工具，要簡單了解有哪些模型以及如何優化模型，務必熟記overfit應對   |
|   AI Platform   |   ⭐⭐     |  在GCP上如何訓練模型，包含自製(Tensorflow) & Google已經build好的一些模型使用  |
|   Cloud Function   |   ⭐     |   Serverless服務，也常整合Pub/Sub 做一些告警 |
|   Cloud Dataprep   |   ⭐⭐     |  資料前處理，適合給沒有coding 經驗的人使用(ex 分析師)     |
|   Data Composer   |    ⭐⭐    | 就是Airflow，在不同服務兼的任務相依性可做調配     |
|   Datalab -> Vertex AI Workbench   |   ⭐     |  類Jupyter，完全沒用過...    |
|   Cloud Storage   |  ⭐⭐⭐      |  存放資料的工具，常考分派權限 & 備份使用    |
|   Cloud Logging   |  ⭐⭐      | 除錯、檢查user有哪些操作常用   |
|   DataStudio   |    ⭐    | 資料視覺化工具，常與Bigquery搭配    |
|   Cloud Fusion   |   ⭐⭐     | 完全沒念到，甚至不知道這是什麼工具，卻考了兩題出來...     |
|   Dialogflow   |   ⭐     | chatbot 服務，完全沒念到，也考了一題出來，會整合AI Platform裡的預處理模型(ex 語音轉文字)    |

另外也常問的問題包含從本地端遷移上雲、權限設置(IAM)、怎樣減少成本等問題，這些就是每個工具各自有需要熟悉的地方了。

## 考題 

* [Google 官方的模擬試題](https://docs.google.com/forms/d/e/1FAIpQLSfkWEzBCP0wQ09ZuFm7G2_4qtkYbfmk_0getojdnPdCYmq37Q/viewform)
> 約20題，有附上文件以及錯誤選項為什麼不對的說明，第一次寫考題推薦先練習這份，畢竟這一定最接近官方的考試

* [Examtopics](https://www.examtopics.com/exams/google/professional-data-engineer/view/1/)
> 考古題網站，因為時間不太夠所以後來我只看這個，針對每個題目做Tag和筆記，每5題要填一次機器人認證，大概看到一半左右會要求註冊帳號，到更後面約Topic2就要付費了。
另外答案錯誤率頗高，需要看網友討論才能確定是否為正確答案，有些問題會因為年代差異而有所分歧(ex 早年BQ不支援table的權限設定，所以有人會認為權限控管須設在dataset)，這些都是要注意的地方。
非常推薦閱讀這份考題，我考試時大概有1/5左右的題目是在上面閱讀過的，且可以透過這份考題琢磨常考重點。
我自己做筆記的情況大概會分成自己的熟練度/考題類型/其他人的討論文件等等。
![自己做的筆記](https://i.imgur.com/j6oaxwL.png)

* [Udemy](https://www.udemy.com/course/google-cloud-professional-data-engineer-gcp-exams)
> 上面的考題唸完後，在網路上試著買了這份來考看看，不過最後我沒有全部做完，題目相對簡單且解說很少，不是很推薦。

  
以上就是這次的分享，再次覺得自己很幸運可以一次通過! 考試只是一個證明，實務操作上還有更多細節需要發想和面對呢。