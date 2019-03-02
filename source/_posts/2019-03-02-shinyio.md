---
title: shinyapps.io檔案存放
date: 2019-03-02 10:09:54
tags: 
    - R
    - shiny
    - shinyapps.io
---



## 需求
建立一個使用者可以上傳分數，看到目前比賽分數的平台，
需要紀錄每次使用者上傳的分數以及上傳時間。

![範例圖片](https://i.imgur.com/xKe7t11.png)

## 遇到的問題
Shiny寫出檔案到當下路徑會定時被還原，查了發現是shinyapps.io不允許本地檔案存儲，因此要調到其他儲存平台。
使用自己的shiny server不會有這種問題。
參照 [Persistent data storage in Shiny apps](http://shiny.rstudio.com/articles/persistent-data-storage.html)


`
When going through the different storage type options below, keep in mind that if your Shiny app is hosted on shinyapps.io, you will have to use a remote storage method for the time being. RStudio plans to implement persistent storage on shinyapps.io soon. In the meantime, using local storage is only an option if you’re hosting your own Shiny Server, though that comes at the price of having to manage a server and should only be done if you’re comfortable with administering a server.
`

## 解決辦法
安裝googlesheets包做資料存儲/讀取，由於我的數據是小量數據(最多不會超過幾百筆)，因此googlesheet就夠用了。
大量數據建議還是導入資料庫存儲。


## 範例程式碼

### server.R
### ui.R
### global.R






