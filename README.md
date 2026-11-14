# 造市練習台 Market-Making Practice

一個在瀏覽器裡玩的造市（market making）練習遊戲。你報 bid / ask，看得到答案的知情者和隨機買賣的散戶會來成交，結算後告訴你每一輪該報多少。

A single-page market-making drill: quote a two-sided market on a hidden sum while an informed trader and a noise trader trade against you. The interface is in Traditional Chinese.

## 玩法

- **標的：** 4 顆骰子、3 張牌或 5 張牌的總和，每輪公開一個。
- **每輪：** 填整數的 bid 和 ask，價差不能超過上限。可以順便填你估的 fair value。
- **對手：**
  - 知情者看得到總和。總和高於你的 ask 就買，低於你的 bid 就賣，有利可圖時有一定機率出手。
  - 散戶什麼都不知道，每輪 25% 買 1 單位、25% 賣 1 單位、50% 不動。
  - 成交時你只看得到總量，不知道是誰。
- **結算：** 顯示每一輪含成交資訊的 fair value（對每筆成交與每次沒成交做 Bayes 更新）、單輪期望值最佳的報價、實際是誰跟你成交，以及損益。

## 怎麼看成績

損益受運氣影響很大。比較可靠的指標是 **EV 差距**：你的報價與單輪最佳報價的期望值差，越接近 0 越好。

三種難度的差別是價差上限和知情者的出手機率與數量。每輪都報最佳價時，「入門」平均小賺，「標準」大致打平，「困難」的期望值是負的，目標是少賠。

## 限制

- 「單輪最佳」只計算當輪的期望值，沒有考慮部位風險，所以不會建議你為了庫存去 skew 報價。
- 累計成績存在瀏覽器的 localStorage，換裝置不會同步。

## 在本機執行

整個遊戲就是 `index.html` 一個檔案，沒有建置步驟，用瀏覽器直接開啟即可。字型從 Google Fonts 載入，離線時會退回系統字型。
