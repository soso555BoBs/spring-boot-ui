# 雑記
- 以下 [2.] の途中！ 2021/02/15 12:17
1. curl でも spring starter 使えるんだね
    - ```$ mkdir ui && cd ui```
    - ```$ curl https://start.spring.io/starter.tgz -d style=web -d style=security -d name=ui | tar -xzvf -```
2. Angular を使えるようにする
    - ここにやり方書いてある
        - https://github.com/dsyer/spring-boot-angular
    1. pom.xml に以下を追記

```
        <plugin>
            <groupId>com.github.eirslett</groupId>
            <artifactId>frontend-maven-plugin</artifactId>
            <version>1.6</version>
            <configuration>
                <nodeVersion>v9.11.2</nodeVersion>
            </configuration>
            <executions>
                <execution>
                    <id>install-npm</id>
                    <goals>
                        <goal>install-node-and-npm</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
```

    2. プロジェクトを右クリック > [Maven] > [プロジェクトを更新]
    3. プロジェクトディレクトリに移動する（ターミナル）
    4. 以下で Angular CLI をインストールする

```
$ cat > npm
#!/bin/sh
cd $(dirname $0)
PATH="$PWD/node/":$PATH
node "node/node_modules/npm/bin/npm-cli.js" "$@"
$ chmod +x npm
$ ./npm install @angular/cli
```

    5. 