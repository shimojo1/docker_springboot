Docker-SpringBoot
------------

DockerでSpringBootの実行環境を作成できるパッケージです。

### 環境作成方法

Ubuntu20.04環境で実行確認済

ファイル構成は以下
```
docker-springboot
├── docker-compose.yml
├── java
│   └── Dockerfile
├── mysql
│   ├── Dockerfile
│   ├── data
│   ├── initdb
│   └── my.cnf
└── workspace
    └── empty
```

1. workspace以下にSpringBootのプロジェクトを配置する(プロジェクトのディレクトリ名をXXXXXとする)

2. docker-compose を行う
```
docker compose up -d
```

3. SpringBootプロジェクトをビルドしてjarファイルを作成
```
docker exec --workdir /workspace/XXXXX -it springboot_app sh mvnw package spring-boot:repackage
```

4. 作成されたjarからSpringBootプロジェクトを起動
```
docker exec --workdir /workspace/XXXXX/target -it springboot_app java -jar XXXXX-0.0.1-SNAPSHOT.jar
```
