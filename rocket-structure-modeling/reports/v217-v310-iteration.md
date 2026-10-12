# GR25 v217 → v310：兩個快照的迭代差異 / Snapshot change record

此報告只比較提供的兩個 STEP 匯出檔。沒有 v218–v309 的檔案、原生 CAD 時間軸或提交紀錄，不能重建中間每次修改。 / Only two STEP exports are available; intermediate edits and their sequence cannot be reconstructed.

## 快照與來源 / Snapshot provenance

| 項目 / Item | v217 | v310 |
|---|---|---|
| 來源檔名 / Source filename | assemblage v217.step | assemblage v310.step |
| 內部 FILE_NAME / Internal filename | assemblage v217.step | assemblage v60.step |
| 原始匯出時間 / Original export timestamp | 2024-09-30T15:01:28+02:00 | 2025-06-01T01:22:12+02:00 |
| 前處理器 / Preprocessor | ST-DEVELOPER v20 | ST-DEVELOPER v20.1 |
| 匯出系統 / Originating system | Autodesk Translation Framework v13.20.0.188 | Autodesk Translation Framework v14.10.0.0 |
| 位元組 / Bytes | 119421065 | 144446569 |
| SHA-256 | edc8f3edf5881433e60946a62d565e511818be0585da313c0c0dae7f66dcda86 | 1eaf7aa77d721a60669dca6b7cdf336997512613ba6a9508685e8926657ab3d1 |
| 實體 instance / Entity instances | 1989498 | 2264150 |
| PRODUCT 記錄 / Product records | 3558 | 3644 |
| 組立 usage edge / Assembly usage records | 5043 | 5261 |
| 正規化 family / Normalized label families | 2363 | 2427 |

v310 是外部檔名的快照標籤；該檔內部 FILE_NAME 是 `assemblage v60.step`，頂層 PRODUCT 是 `assemblage v60`。個人化輸出採用 GR25 v310 名稱，原始 v60 名稱仍可由 inventory 與命名對照記錄追溯。 / The v310 filename identifies the supplied snapshot; its original header and top PRODUCT identify v60. The personalized output uses GR25 v310 while inventories and naming records retain the original v60 provenance.

## 可確認的時間點 / Recorded timeline

| 日期 / Date | 來源 / Evidence | 記錄 / Event |
|---|---|---|
| 2024-09-30 | v217 原始 STEP FILE_NAME timestamp | 該快照 header 記錄的匯出日期 / Header-recorded export date |
| 2025-06-01 | v310 原始 STEP FILE_NAME timestamp | 該快照 header 記錄的匯出日期；內部名稱 v60 / Header-recorded export date; internal v60 label |
| 2026-10-11 | 本 repo 個人化工作 / Repository personalization | 名稱改為繁中／英文、建立對照與快照差異報告；不是新增幾何迭代 / Bilingual naming and evidence reports; no geometry revision |

匯出日期取自原始 STEP header，沒有獨立驗證其時鐘。日期之間的修改次序與 v218–v309 事件沒有來源證據。 / Export dates come from the original headers; intermediate events and edit order are unknown.

## 比對規則與可確認差異 / Matching and observed changes

以 PRODUCT 的 name（第二欄）去除末尾 `:實例編號` 與 `v版本數字` 後進行大小寫精確比對。`#entity` 編號只用於各檔內追溯，不作跨檔身份識別。PRODUCT ID 的 `_n` 去重尾碼不作 family 比對依據。 / Matching uses exact, case-sensitive PRODUCT name families after removing terminal occurrence/version suffixes. Entity numbers are only local references.

- 僅出現在 v310 的 family / Added labels: **88**。
- 僅出現在 v217 的 family / Removed labels: **24**。
- 兩檔都有的 family / Matched labels: **2339**。
- 記錄數量改變 / Record-count changes: **14**。
- 版本標籤集合改變 / Version-label-set changes: **52**。

新增與消失是名稱集合的差異，可能包含重新命名、匯出方式或內容變動；不等於已證明的實體零件新增與刪除。數量指 PRODUCT 記錄數與直接組立 usage edge 數，不是展開後的 BOM 用量。 / Added/removed labels may reflect renaming or export changes; counts are records and direct assembly edges, not flattened BOM quantities.

## 可追溯的系統線索 / Subsystem observations

以下僅描述原始名稱中的線索，不宣稱已確認功能、裝配替代關係或幾何等價。 / These observations concern the supplied labels and do not establish functional replacement or geometric equivalence.

- 緊固件型號 / Purchased-fastener labels: 23 個供應商式型號 family 新出現，4 個消失；詳見 added/removed CSV。 / 23 vendor-style part families appear and 4 disappear.
- 機構名稱 / Mechanism labels: v310 新出現 `ActionneurCoude`, `ActionneurDroit`, `BagueLiberation`, `EcrouVerrouillage`, `PignonLiberation`, `TigeVerrouillage`, `PorteMecanisme`; v217 的 `Actionneur` 未匹配。
- 攝影與電池名稱 / Camera and battery labels: v310 新出現 `RunCam_DVR`, `Runcam Nano`, `Support - Camera V2`, `Smart G2 30C LiPos`; v217 的 `TATTU 1300mah 3s`, `tattu 1300MHa 3s LiPo`, `BMS 3S 40A` 未匹配。
- PCB 介面名稱 / PCB interface labels: v310 新出現 `PCB-INTERFACE N1`, `PCB-INTERFACE N2`, `PCB_INTERFACE_OBC_PCB`, `PCB_interface_moteur_PCB`。
- 命名歧義 / Naming ambiguity: `trappe` → `Trappe` 的大小寫差異會形成消失與新增各一列；`CasePara n°3`、`CasePara`、`CasePara_top` 也未自動判定為同一零件。 / Potential rename pairs remain unmatched for engineering review.
- 大量既有 family 的版本數字降低或重設為 v1；不能從 v217/v310 的外部檔名推定所有子零件版本都往上遞增。 / Many matched labels decrease or reset to v1; snapshot filenames do not imply monotonic component revisions.

## 記錄數量變更 / Record-count changes

| 原始 family / Family | PRODUCT v217 → v310 | Usage edge v217 → v310 |
|---|---:|---:|
| 鋼製六角螺帽 90592A085 / Steel Hex Nut 90592A085 (90592A085_Steel Hex Nut) | 15 → 9 | 63 → 37 |
| 鋼製六角螺帽 90592A085 (1) / Steel Hex Nut 90592A085 (1) (90592A085_Steel Hex Nut (1)) | 5 → 3 | 12 → 10 |
| 合金鋼內六角圓柱頭螺絲 91290A117 / Alloy Steel Socket Head Screw 91290A117 (91290A117_Alloy Steel Socket Head Screw) | 3 → 3 | 24 → 19 |
| 合金鋼內六角圓柱頭螺絲 91290A123 / Alloy Steel Socket Head Screw 91290A123 (91290A123_Alloy Steel Socket Head Screw) | 2 → 4 | 9 → 18 |
| 合金鋼內六角圓柱頭螺絲 91290A171 / Alloy Steel Socket Head Screw 91290A171 (91290A171_Alloy Steel Socket Head Screw) | 1 → 2 | 4 → 6 |
| C5 支撐環 n°2 / C5 Support Ring n°2 (AnneauSupportC5 n°2) | 1 → 2 | 1 → 2 |
| 桿件座塊 / Rod Block (BlocTige) | 1 → 1 | 2 → 1 |
| 攝影機 / Camera (Camera) | 2 → 2 | 4 → 3 |
| 攝影機支架 / Camera Holder (Camera-holder) | 4 → 3 | 4 → 3 |
| 304 不鏽鋼自鎖六角螺帽組立 Ø4 / 304 Stainless Self-locking Hex Nut Assembly Ø4 (Ecrou_Hex_auto-freine_Assemblage_Ecrou frein inox 304 Ø4) | 1 → 1 | 69 → 48 |
| 載荷外蒙皮 N1 / Payload Skin N1 (PeauChargeUtile N1) | 1 → 1 | 2 → 3 |
| 分離區外蒙皮 / Separation Skin (PeauSeparation) | 1 → 1 | 1 → 2 |
| 頂出銷 / Ejection Pin (PinEjection) | 1 → 1 | 4 → 6 |
| 攝影機電子件 / Camera Electronics (elecCamera) | 1 → 1 | 4 → 3 |

## 版本標籤變更 / Version-label changes

`×` 表示具有該版本標籤的 PRODUCT 記錄數。 / × denotes the number of PRODUCT records carrying that label.

| 原始 family / Family | v217 原始版本標籤 / Original labels | v310 原始版本標籤 / Original labels |
|---|---|---|
| 紅色母扁插端子 22-16 / Red Female Flat Spade 22-16 (22-16 female flat spade red) | v2 × 1 | v1 × 1 |
| 組立 ASS-C0 / Assembly ASS-C0 (ASS-C0) | v22 × 1 | v1 × 1 |
| 組立 ASS-C3 / Assembly ASS-C3 (ASS-C3) | v101 × 1 | v1 × 1 |
| 組立 ASS-C6 / Assembly ASS-C6 (ASS-C6) | v39 × 1 | v2 × 1 |
| 組立 ASS_C1 / Assembly ASS_C1 (ASS_C1) | v101 × 1 | v22 × 1 |
| 組立 ASS_C10 / Assembly ASS_C10 (ASS_C10) | v8 × 1 | v2 × 1 |
| 組立 ASS_C7 / Assembly ASS_C7 (ASS_C7) | v41 × 1 | v6 × 1 |
| 環件 / Ring (Anneau) | v5 × 1 | v1 × 1 |
| 下部環件 / Lower Ring (Anneau - Bas) | v22 × 1 | v1 × 1 |
| 止回環 / Anti-return Ring (Anneau antiretour) | v22 × 1 | v1 × 1 |
| 結構環 / Structural Ring (Anneau structure) | v5 × 1 | v1 × 1 |
| C5 支撐環 / C5 Support Ring (AnneauSupportC5) | v8 × 1 | v1 × 1 |
| C5 支撐環 n°2 / C5 Support Ring n°2 (AnneauSupportC5 n°2) | v6 × 1 | v2 × 2 |
| 最終版環件 / Final Ring (Anneau_final) | v19 × 1 | v1 × 1 |
| 組立 / Assembly (Assemblage) | v12 × 1 | v1 × 1 |
| 閉合環 / Closure Ring (Bague-fermeture) | v38 × 1 | v18 × 1 |
| 載荷整流罩底座 / Cargo Fairing Base (Base coiffe cargo) | v26 × 1 | v8 × 1 |
| 臂件 / Arm (Bras) | v21 × 1 | v1 × 1 |
| 攝影機 / Camera (Camera) | v1 × 2 | v1 × 1, v2 × 1 |
| 攝影機支架 / Camera Holder (Camera-holder) | v26 × 3, v35 × 1 | v3 × 3 |
| FPV 外殼 / FPV Case (Case FPV) | v52 × 1 | v1 × 1 |
| 修改版整流罩 / Modified Fairing (Coiffe_mod) | v7 × 1 | v1 × 1 |
| 馬達蓋 / Motor Cover (CouvreMoteur) | v3 × 1 | v1 × 1 |
| OLED 顯示器 0.96_128x64 / OLED Display 0.96_128x64 (Display_OLED_0.96_128x64) | v4 × 1 | v1 × 1 |
| 導引偏置件 1 / Guide Offset Part 1 (Déport guide 1) | v4 × 1 | v1 × 1 |
| 導引偏置件 2 / Guide Offset Part 2 (Déport guide 2) | v20 × 1 | v9 × 1 |
| 導引偏置件 3 / Guide Offset Part 3 (Déport guide 3) | v14 × 1 | v1 × 1 |
| 電子零件支架 / Electronics Holder (Elec_Holder) | v19 × 1 | v6 × 1 |
| 閉合件 / Closure (Fermeture) | v32 × 1 | v8 × 1 |
| 人機介面 IHM / Human-machine Interface IHM (IHM) | v32 × 1 | v1 × 1 |
| 人機介面電子件 IHM / IHM Electronics (IHMElec) | v17 × 1 | v1 × 1 |
| 規格元件 M3 634mm / Specified Component M3 634mm (M3 634mm) | v2 × 1 | v1 × 1 |
| 元件 MB1430-G431KBT6-A02 / Component MB1430-G431KBT6-A02 (MB1430-G431KBT6-A02) | v2 × 1 | v1 × 1 |
| MotorShield 印刷電路板 / MotorShield PCB (MotorShield-pcb) | v3 × 1 | v1 × 1 |
| 墊塊 / Pad (Patin) | v2 × 1 | v1 × 1 |
| 載荷外蒙皮 N1 / Payload Skin N1 (PeauChargeUtile N1) | v12 × 1 | v1 × 1 |
| 分離區外蒙皮 / Separation Skin (PeauSeparation) | v12 × 1 | v1 × 1 |
| 降落傘板件 / Parachute Plate (Plaque Parachute) | v4 × 1 | v1 × 1 |
| MSE 電路板支架 n°3 / MSE PCB Holder n°3 (Porte_PCB_n°3 MSE) | v7 × 1 | v1 × 1 |
| MSE 電路板支架 n°4 / MSE PCB Holder n°4 (Porte_PCB_n°4 MSE) | v13 × 1 | v1 × 1 |
| RBF 結構件 / RBF Structure (RBF-structure) | v2 × 1 | v1 × 1 |
| 電子區環件 / Electronics Ring (RingElec) | v19 × 1 | v1 × 1 |
| 補強支架 / Reinforcement Support (SupportRenfort) | v15 × 1 | v9 × 1 |
| 微動開關 V-156-1C25 / Micro Switch V-156-1C25 (V-156-1C25 micro switch) | v4 × 1 | v1 × 1 |
| 螺絲 Vis_ID_2 / Screw Vis_ID_2 (Vis_ID_2) | v4 × 1 | v1 × 1 |
| 元件 accelero-contact / Component accelero-contact (accelero-contact) | v31 × 1 | v1 × 1 |
| 翼片 n°2 / Fin n°2 (aileron n°2) | v2 × 1 | v1 × 1 |
| GR25 組立 v310 / GR25 Assembly v310 (assemblage) | v217 × 1 | v60 × 1 |
| 下部聯接件 / Lower Coupling (couplage_bas) | v74 × 1 | v2 × 1 |
| 攝影機電子件 / Camera Electronics (elecCamera) | v3 × 1 | v1 × 1 |
| 內部結構 / Internal Structure (structureInterne) | v35 × 1 | v14 × 1 |
| 電子區艙門複本 / Electronics Hatch Copy (trappeElec Copier) | v3 × 1 | v1 × 1 |

## 匯出結構與單位 / Export structure and units

| Entity type | v217 | v310 |
|---|---:|---:|
| MANIFOLD_SOLID_BREP | 2458 | 2541 |
| BREP_WITH_VOIDS | 1 | 2 |
| SHELL_BASED_SURFACE_MODEL | 18 | 419 |
| CLOSED_SHELL | 2460 | 2547 |
| ADVANCED_FACE | 54009 | 58007 |
| EDGE_CURVE | 141195 | 152989 |
| VERTEX_POINT | 93031 | 101507 |
| CARTESIAN_POINT | 542655 | 716631 |
| DIRECTION | 270937 | 288269 |

兩檔皆可觀察到毫米與公尺的長度 SI_UNIT 定義、公斤質量單位、弧度與球面度。匯出資料包含不只一種長度單位，需依 representation context 解讀；本報告未假定整個檔案所有數值都是毫米。 / Both files declare millimetres, metres, kilograms, radians and steradians; values must be interpreted in their representation contexts.

實體類型數量增加是匯出結構的可確認差異。匯出器版本也不同，因此只憑數量不能推定幾何修訂、品質改善或零件體積改變。本報告沒有作體積、重量、包圍盒或幾何等價分析。 / Entity counts differ and exporter versions differ; those counts alone do not establish geometric changes.

## 完整可機讀證據 / Machine-readable evidence

- [v217 inventory](v217-inventory.json) / [v310 inventory](v310-inventory.json)：PRODUCT、組立關係、原始名稱、local entity refs、entity counts、header 與 units。
- [Snapshot comparison](v217-v310-comparison.json)：完整 added/removed families、數量與版本差異及未匹配資料。
- [Added families](added-families.csv) / [Removed families](removed-families.csv)。
- [Quantity changes](quantity-changes.csv) / [Version-label changes](version-label-changes.csv)。
- [Entity type count changes](entity-type-count-changes.csv)。

CSV 的中文、英文欄位只在載入翻譯對照表後填入；原始 family 永遠保留以利重現。 / Bilingual CSV fields are populated only when a translation mapping is supplied; original families are retained.

## CAD 核心補充證據 / Additional CAD kernel evidence

[原始快照 CAD 核心比較](cad-snapshot-comparison.md) 提供獨立 OCP 匯入後的拓樸數量、全域分析包圍盒與沿軸 span。兩個快照沒有做剛體配準，因此包圍盒差異不能直接解讀成逐零件尺寸改動；沒有比較體積、面積或重量。 / The additional source-import report records topology and global bounds; the snapshots were not aligned and no part-dimension, comparative volume, area or mass claim is made.
