# Small digital pseudo lock-in amp — JLCPCB実装

## 発注条件

PCB **5枚**、PCBA **2枚**、**Top Side / Standard PCBA**。銅箔4層、90 × 65 mm、1.6 mm、FR-4、緑レジスト、ENIG。WS2812B-V6はJLCPCBのStandard専用部品です。標準実装の捨て基板・フィデューシャル・治具穴はJLCPCB追加を選択します。 [WS2812B-V6](https://jlcpcb.com/partdetail/Worldsemi-5_0mmx5_0mm/C52917433) · [JLCPCBの実装条件](https://jlcpcb.com/help/article/terms-and-conditions-of-jlcpcb-assembly-service)

- 基板データは `Small_digital_pseudo_lockinamp_JLCPCB_PCBA.zip`。実装するパッドだけを含む表面ペースト層を同梱しています。
- BOMは `BOM_JLCPCB.csv`、座標は `CPL_JLCPCB.csv`。基板1枚あたり126箇所で、両ファイルの部品番号は一致しています。座標はmmでGerber・ドリルと共通の原点です。
- 実装プレビューでD101〜D103・IC801・U101のピン1、J102〜J104の差し込み方向を確認してください。回転の照合にはJLCEDA/EasyEDA公式ライブラリのパッド配置を使用しました。 [JLCEDA](https://lceda.cn/) · [EasyEDA](https://easyeda.com/) · [JLCPCBのBOM・CPLガイド](https://jlcpcb.com/help/article/how-to-generate-the-bom-and-centroid-file-from-kicad)

## 手実装と未実装

| 部品番号 | 品名・扱い | 実装2枚分 |
|---|---|---:|
| C306, C506, C706 | 62 pF・C0G・0603（例 CL10C620JB8NNNC） | 6 |
| IC101, IC303, IC304, IC305, IC503, IC504, IC505, IC703, IC704, IC705 | NJM2732E（SOP-8、テープ品はNJM2732E-TE1） | 20 |
| IC201, IC401, IC601 | ADS8331IBPWR（Bグレード、TSSOP-24） | 6 |
| IC301, IC302, IC501, IC502, IC701, IC702 | TMUX1101DBVR（SOT-23-5、公開在庫2個） | 12 |
| J101 | Raspberry Pi Pico（RP2040、ピンヘッダなし） | 2 |
| R301, R302, R501, R502, R701, R702 | TBD（ゲイン設定用。値が決まるまで未実装） | 未実装 |

ICの元の型番とグレードを維持しています。C306・C506・C706の62 pF C0Gは、調べたJLCPCBの0603候補で2枚に必要な6個の在庫を確認できなかったため手実装です。TBDのゲイン抵抗は値を確定するときに取り付けます。 [TMUX1101の公開カタログ](https://jlcpcb.com/partdetail/C1852057) · [62 pFの公開カタログ](https://jlcpcb.com/partdetail/C62683)

## 選定部品と概算

2026年11月18日（日本時間）のJLCPCB公開カタログ。20品種のうちBasicは10品種です。公開単価×搭載数では**2枚分で $8.58**です。PCB代、実装料、部品種ごとのセットアップ料、ロス分、手実装部品、送料は別です。

| 仕様・品名 | メーカー型番 | 区分 | 2枚分 | 公開在庫 | 公開単価（USD） | JLCPCB |
|---|---|---|---:|---:|---:|---|
| 100nF 50V X7R | CC0603KRX7R9BB104 | Basic | 56 | 31,601,936 | $0.0056 | [`C14663`](https://jlcpcb.com/partdetail/C14663) |
| 1uF 50V X5R | CL10A105KB8NNNC | Basic | 14 | 12,403,632 | $0.0095 | [`C15849`](https://jlcpcb.com/partdetail/C15849) |
| 22uF 16V X5R | CGA0603X5R226M160JT | Extended | 6 | 47,492 | $0.0425 | [`C6119868`](https://jlcpcb.com/partdetail/C6119868) |
| 150pF 50V C0G 5% | CL10C151JB8NNNC | Extended | 6 | 3,910 | $0.0289 | [`C37298`](https://jlcpcb.com/partdetail/C37298) |
| 180pF 50V C0G 5% | CL10C181JB8NNNC | Extended | 6 | 5,644 | $0.0132 | [`C17096`](https://jlcpcb.com/partdetail/C17096) |
| 470pF 50V C0G 5% | CL10C471JB81PNC | Extended | 6 | 3,837 | $0.0118 | [`C472795`](https://jlcpcb.com/partdetail/C472795) |
| 220pF 50V C0G 5% | CC0603JRNPO9BN221 | Extended | 12 | 510,309 | $0.0076 | [`C106210`](https://jlcpcb.com/partdetail/C106210) |
| 10nF 50V X7R | 0603B103K500NT | Basic | 6 | 4,967,344 | $0.0103 | [`C57112`](https://jlcpcb.com/partdetail/C57112) |
| WS2812B-V6 | — | Extended | 6 | 45,127 | $0.0860 | [`C52917433`](https://jlcpcb.com/partdetail/C52917433) |
| MCP23S17-E/SS | — | Extended | 2 | 238 | $1.6378 | [`C148009`](https://jlcpcb.com/partdetail/C148009) |
| S02B-XASS-1N-BN(LF)(SN) | — | Extended | 6 | 2,150 | $0.2783 | [`C161669`](https://jlcpcb.com/partdetail/C161669) |
| 10k ohm 1% | 0603WAF1002T5E | Basic | 74 | 44,272,430 | $0.0019 | [`C25804`](https://jlcpcb.com/partdetail/C25804) |
| 4.7k ohm 1% | 0603WAF4701T5E | Basic | 14 | 14,757,559 | $0.0028 | [`C23162`](https://jlcpcb.com/partdetail/C23162) |
| 120 ohm 1% | 0603WAF1200T5E | Basic | 2 | 2,266,360 | $0.0020 | [`C22787`](https://jlcpcb.com/partdetail/C22787) |
| 100k ohm 1% | 0603WAF1003T5E | Basic | 12 | 14,002,981 | $0.0029 | [`C25803`](https://jlcpcb.com/partdetail/C25803) |
| 6.2k ohm 1% | 0603WAF6201T5E | Basic | 12 | 535,692 | $0.0023 | [`C4260`](https://jlcpcb.com/partdetail/C4260) |
| 1k ohm 1% | 0603WAF1001T5E | Basic | 6 | 31,413,255 | $0.0017 | [`C21190`](https://jlcpcb.com/partdetail/C21190) |
| TS-1088-AR02016 | — | Basic | 2 | 843,895 | $0.0516 | [`C720477`](https://jlcpcb.com/partdetail/C720477) |
| MLD-TS-6X6X5-J | — | Extended | 2 | 2,475 | $0.0133 | [`C52750873`](https://jlcpcb.com/partdetail/C52750873) |
| MCP1541T-I/TT | — | Extended | 2 | 2,260 | $0.7764 | [`C7375`](https://jlcpcb.com/partdetail/C7375) |

ADC基準電圧用のC201・C401・C601は、現行の0603ランドに合わせて22 µF・16 V品を選定しました。4.096 V印加時の実効容量と基準電圧の整定は実機で確認する項目です。TIのレイアウト例は22 µFの0805品を使用しています。 [ADS8331データシート](https://www.ti.com/lit/ds/symlink/ads8331.pdf)
