# GR25：CAD 核心快照證據 / CAD kernel snapshot evidence

本報告描述兩個原始 STEP 的獨立匯入結果，補充名稱與 entity 記錄比較。此處比較 v217 與 v310 原始快照；同版本原檔與雙語輸出的保真驗證另見 `cad-validation.json` 與 `validation.json`。 / This report compares the original snapshots; source-to-bilingual preservation audits are separate.

核心 Python binding / Kernel binding: **OCP 7.9.3.0**。
來源 / Fingerprint evidence: `reports/cad-validation.json`。

## 原始來源與匯入 / Sources and imports

| Item | v217 | v310 |
|---|---|---|
| Repository source | `sources/v217.step` | `sources/v310.step` |
| Supplied source filename | `assemblage v217.step` | `assemblage v310.step` |
| SHA-256 | `edc8f3edf5881433e60946a62d565e511818be0585da313c0c0dae7f66dcda86` | `1eaf7aa77d721a60669dca6b7cdf336997512613ba6a9508685e8926657ab3d1` |
| ReadFile status | IFSelect_RetDone | IFSelect_RetDone |
| Candidate roots / transferred roots | 1 / 1 | 1 / 1 |
| Result shapes | 1 | 1 |
| STEP entity count | 1989498 | 2264150 |

兩個快照皆成功匯入並轉換全部候選 root。模型沒有重新匯出。v310 是使用者提供的檔名標籤；原始內部 v60 名稱差異仍保留在 [快照迭代報告](v217-v310-iteration.md)。 / Both original files imported and transferred all candidate roots; no model was re-exported. The original v310/v60 naming discrepancy remains documented.

## 匯入後拓樸數量 / Imported indexed topology

| Topology | v217 | v310 | v310 − v217 |
|---|---:|---:|---:|
| compounds | 1 | 1 | +0 |
| compsolids | 0 | 0 | +0 |
| solids | 4,477 | 4,768 | +291 |
| shells | 4,498 | 5,995 | +1,497 |
| faces | 114,654 | 129,196 | +14,542 |
| wires | 123,979 | 139,520 | +15,541 |
| edges | 293,054 | 336,152 | +43,098 |
| vertices | 188,956 | 219,376 | +30,420 |

這些是 Open CASCADE indexed shape map 的拓樸指紋。帶不同組立 placement 的匯入 shape 可有不同索引；solid 數量不等於不同設計零件數，也不是展開後 BOM。 / These are indexed kernel shape counts under the imported placements, not engineering-part identities or flattened BOM quantities.

## 全域分析包圍盒 / Analytic global bounding boxes

單位為毫米；STEP reader 以 `SetSystemLengthUnit(1.0)` 設定系統長度單位。以 `BRepBndLib.Add(shape, box, False)` 計算保守分析包圍盒，包含 subshape tolerance，未使用三角網格。表格小數顯示 6 位，JSON 保留原始精度；顯示位數不是量測精度。 / Values are millimetres in the reader's system unit. The analytic conservative box includes shape tolerances and uses no triangulation; formatting does not imply measurement accuracy.

| Global axis | v217 min | v217 max | v217 span | v310 min | v310 max | v310 span | Span difference |
|---|---:|---:|---:|---:|---:|---:|---:|
| X | -1019.632777 | -506.724196 | 512.908581 | -328.717234 | 231.955103 | 560.672337 | +47.763756 |
| Y | -931.565874 | 1311.734129 | 2243.300003 | -245.979730 | 2091.320273 | 2337.300003 | +94.000000 |
| Z | 123.143028 | 683.456796 | 560.313768 | -84.141991 | 428.444775 | 512.586766 | -47.727002 |

兩檔保留各自儲存的全域座標、組立位置與方向；本報告沒有做剛體配準。包圍盒座標及沿軸 span 的差異會受到全域配置、方向與幾何影響，不能單憑這張表認定某零件尺寸被修改。 / The snapshots retain their own stored coordinates, placements and orientations and were not rigidly aligned. These boxes do not establish specific part-dimension edits.

## 分析範圍 / Scope

- 已確認 / Observed: source SHA-256、成功匯入、root transfer、indexed topology counts、global conservative box 與沿軸 span。
- 沒有進行 / Not performed: 跨版本零件對應、剛體配準、Boolean geometry difference、逐零件尺寸分析或中間迭代歷史重建。
- v217 baseline 有選配體積／面積積分，v310 baseline 沒有；本報告不比較體積、面積或重量。積分也不是實際材料質量或經過 Boolean union 的組立體積。 / No comparative volume, area or mass conclusion is made.

[完整 JSON / Full-precision evidence](cad-snapshot-comparison.json) · [名稱與結構差異 / Label and entity comparison](v217-v310-iteration.md)
