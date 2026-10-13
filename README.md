# GR25

GR25 保存火箭專案的建模、結構設計與電路板設計資料，包括 CAD 快照、PCB 工程檔、製造輸出與設計檔案整理紀錄。這是一個硬體設計資料庫，不是可直接執行的飛控軟體發行版。

## 工作範圍

我在此專案對應的工作範圍為**建模、結構設計與電路板設計**。部分原始工作檔已遺失，因此以目前仍保留的設計檔與來源紀錄說明成果，不將團隊整體成果或未保存證據的航電、飛控、AI 與飛行表現列為本人的已驗證成果。

Repository 也保存團隊材料與可能包含匯入資產的組立檔；檔案存在不代表其中每個零件、板卡或元件均為本人獨立原創。具體歸屬需以原始設計及修改紀錄逐件對應。

## 目錄與閱讀入口

| 路徑 | 內容 |
| --- | --- |
| [rocket-structure-modeling/](rocket-structure-modeling/) | STEP 來源／整理後模型，以及名稱、結構和 CAD 匯入比較紀錄。 |
| [CAD 快照比較](rocket-structure-modeling/reports/cad-snapshot-comparison.md) | v217／v310 的來源指紋、匯入狀態、拓樸與包圍盒；包含分析限制。 |
| [名稱與結構差異](rocket-structure-modeling/reports/v217-v310-iteration.md) | 兩份保留快照的名稱及 entity 比較。 |
| [avionics/hardware/](avionics/hardware/) | PCB 工程與板卡設計檔。此處的目錄名稱不代表飛控功能已完成驗證。 |
| [avionics/fabrication/](avionics/fabrication/) | Gerber、drill 與製造封裝等設計輸出。 |
| [GR25/](GR25/) | 其他保留的原始專案材料。 |
| [gr25.ork](gr25.ork) | 保留的 OpenRocket 專案檔；不等同實際飛行結果。 |

建議先讀 CAD 快照比較與其限制，再依需要開啟 STEP／PCB 原檔。團隊報告等其他材料保留在根目錄，應與個人設計工作分開閱讀。

## 取得大型檔案

大型 STEP、PCB、PDF 與封裝檔使用 Git LFS，規則見 [.gitattributes](.gitattributes)。只有 Git pointer 時，尚未取得真正的設計檔案；GitHub 文字頁面也未必能預覽這些格式。

在已安裝 Git LFS、且有本庫與 LFS 物件存取權限的 checkout 中執行：

```sh
git lfs install
git lfs pull
git lfs ls-files
git lfs fsck
git rev-parse HEAD
```

`git lfs pull` 會下载大型檔案。取得實體後，使用相容的 STEP／PCB 工具開啟；Git clone 成功或 pointer 存在本身不證明 CAD 能正常匯入。LFS 下載與各種 CAD／PCB 軟體的完整相容性仍需在實際環境驗證。

## 設計紀錄的界線

`v217`、`v310` 是保留檔案的版本標籤，不表示已保存 217／310 次設計迭代。雙語名稱整理與同版本保真檢查也不是新的幾何設計成果。

CAD 報告中的 indexed solids、faces 等是匯入後的拓樸指紋，不是独立設計零件數或 BOM。包圍盒差異會受全域座標、組立位置及方向影響；沒有剛體配準與逐件分析時，不能直接推論某零件尺寸改變。

成功匯入、名稱保真、Gerber 或 drill 輸出，只證明各自的檔案／設計輸出範圍，不證明結構強度、實際材料重量、電路通電功能或飛行性能。未保存或未完成的實測，不以模擬或設計值替代。

## 來源與授權

保留既有來源、版本與子目錄授權，例如 [avionics/LICENSE](avionics/LICENSE)。子目錄的授權不可直接推定適用於所有團隊報告、匯入元件或 CAD 資產；本 README 不新增整庫授權，也不改寫原始設計與團隊紀錄。
