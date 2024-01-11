# gradle-flyway-sample
gradleでflywayを使うサンプル

## 使い方
### ローカル
```shell
# マイグレーションの確認
./gradlew flywayInfo

# マイグレーションの実行
./gradlew flywayMigrate

# マイグレーションの削除
./gradlew flywayClean
```

### ローカル以外
```shell
# マイグレーションの確認
./gradlew flywayInfo -PnonLocal=true -Dflyway.password=mysql -Dflyway.placeholders.apiUserPassword=api_user_password

# マイグレーションの実行
./gradlew flywayMigrate -PnonLocal=true -Dflyway.password=mysql -Dflyway.placeholders.apiUserPassword=api_user_password

# マイグレーションの削除
./gradlew flywayClean -PnonLocal=true -Dflyway.password=mysql -Dflyway.placeholders.apiUserPassword=api_user_password
```

## ディレクトリ構成の説明
```
 db // flywayの設定ファイルやマイグレーションファイルを格納するディレクトリ
 ├── config // flywayの設定ファイルを格納するディレクトリ
 │   ├── flyway.properties // ローカル以外の設定ファイル
 │   └── local.properties // ローカルの設定ファイル
 ├── local // ローカルでのみ動かしたいファイルを格納する
 │   └── afterClean.sql // flywayClean実行後に実行するSQL(ローカル専用)
 └── migration
     ├── grant // テーブルの権限管理のためのファイルを格納するディレクトリ
     │   ├── R__grant_for_test2_table.sql
     │   └── R__grant_for_test_table.sql
     ├── master // マスターデータのためのファイルを格納するディレクトリ
     │   └── R__test_table_data.sql
     ├── schema // テーブルの作成や削除のためのファイルを格納するディレクトリ
     │   ├── V1.01__create_test_table.sql
     │   └── V1.02__create_test2_table.sql
     └── user // ユーザー管理のためのファイルを格納するディレクトリ
         └── V1.00__create_api_user.sql
```