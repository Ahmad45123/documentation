---
description: SQL Server データベースでのデータベースモニタリングの設定
disable_sidebar: true
kind: documentation
title: SQL Server の設定
---

### サポートされる SQL Server バージョン

|                 | セルフホスト | Azure     | Amazon RDS | Google Cloud SQL | 注 |
|-----------------|-------------|-----------|------------|------------------|------|
| SQL Server 2012 | {{< X >}}   |           |            |                  | SQL Server 2012 は 2022 年 7 月 12 日にサポートが終了しました。Database Monitoring は、SQL Server 2012 を[既知の制限][1]付きで引き続きサポートします。 |
| SQL Server 2014 | {{< X >}}   | {{< X >}} | {{< X >}}  |                  |      |
| SQL Server 2016 | {{< X >}}   | {{< X >}} | {{< X >}}  |                  |      |
| SQL Server 2017 | {{< X >}}   | {{< X >}} | {{< X >}}  | {{< X >}}        |      |
| SQL Server 2019 | {{< X >}}   | {{< X >}} | {{< X >}}  | {{< X >}}        |      |
| SQL Server 2022 | {{< X >}}   | {{< X >}} | {{< X >}}  | {{< X >}}        |      |

ホスティングタイプを選択して設定の手順を確認します。

{{< partial name="dbm/dbm-setup-sql-server" >}}

<br>

### Agent インテグレーションのオーバーヘッド

Agent インテグレーションのオーバーヘッドテストは、Amazon EC2 マシン `c5.xlarge` インスタンス (4 vCPU、8 GB RAM) で実行しました。テストに使用したデータベースは、Amazon RDS の `db.m5.large` インスタンス (2 vCPU、8 GB RAM) で動作する SQL Server 2019 Standard Edition インスタンスです。このデータベースは、20 個の倉庫を持つ TPC-C ワークロードを実行していました。

| 設定                              | 収集間隔 |
| ------------------------------------ | ------------------- |
| 最小収集間隔のチェック        | 15 秒                 |
| クエリメトリクスの収集間隔    | 60s                 |
| クエリアクティビティの収集間隔 | 10 秒                 |
| 設定の収集間隔         | 600 秒                |

* Agent テストのバージョン: `7.50.2`
* CPU: 平均で CPU の約 1% を使用
* メモリ: 約 300 MiB の RAM を使用 (RSS メモリ)
* ネットワーク帯域幅: 約 40 KB/秒 ▼ | 30 KB/秒 ▲
* Agent によるデータベースへのクエリオーバーヘッド: 約 1% の CPU 時間

[1]: /ja/database_monitoring/setup_sql_server/troubleshooting/#known-limitations