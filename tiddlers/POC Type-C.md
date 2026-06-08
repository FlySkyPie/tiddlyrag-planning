POC Type-C 又稱「EC-BT POC」，引入了 ECS (Entity-Component-System) 架構以及行為樹 (Behavior Tree) 作為 Git Repo 資料探勘智能體的框架，實做了廣度優先遍歷與深度優先遍歷兩種基本範例。

## 說明

為了解決在 [Type-B](<#POC Type-B>)中發現的固定流水線缺陷，需要一種同時具備彈性與可控的演算法。行為樹是已經在遊戲產業與機器人產業使用大約二十年的傳統 AI，技術已經十分成熟，能夠用來適應諸如廠房或是遊戲環境這種複雜環境，同時具備高度的可控性，並且決了有限狀態機 (FSM) 的一些先天缺陷。

行為樹的經典實現是使用一種叫做「黑板模式」的方式來讓智能體取得環境資訊，然而該模式本質上是巨大的 key-value 表，實務上會演變成一個巨大的「局部的全域變數」，因此本 POC 參考 ECS 架構引入當中的 EC 作為資料儲存方式。

## 發現與結論

過程中排除了 [STRIPS](#STRIPS) 模型（包含 [GOAP](#GOAP) 和 [HTN](#HTN) ）兩種算法、並排除了 Utility AI ...等古典 AI 算法，也排除了 [ReAct](#ReAct)，最後選擇行為樹作為 POC 實做標的，主要考量是彈性之餘的可預測性與可控性。

經過條查，釐清了[行為樹解決方案覆蓋範圍](#行為樹解決方案覆蓋範圍)、[行為樹的歷史脈絡](#行為樹的歷史脈絡)。[BehaviorTree.CPP](https://github.com/BehaviorTree/BehaviorTree.CPP) 是其中一個少數滿足作為解決方案條件又沒有被綁定在遊戲引擎的知名函式庫。

探索過程中，將 Git Repo 資料挖掘問題重新定位成[探索與利用問題](#探索與利用問題)，並建議下一步嘗試使用 EC-BT 實做蒙地卡羅樹搜尋 (MCTS, Monte Carlo tree search)。

## 程式碼

[https://github.com/FlySkyPie/tiddlyrag-poc/tree/poc/type-c](https://github.com/FlySkyPie/tiddlyrag-poc/tree/poc/type-c)