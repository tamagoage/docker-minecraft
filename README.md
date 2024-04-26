# Minecraft サーバーのセットアップ

## コンテナ内でコマンド操作だけで立ち上げる方法(docker である必要はない)

1. Ubuntu のコンテナを起動します：

    ```bash
    docker run -it ubuntu bash
    ```

2. 必要なパッケージをインストールします：

    ```bash
    apt install openjdk-21-jre
    apt install tzdata
    ```

3. タイムゾーンを設定します：

    ```bash
    timedatectl set-timezone Asia/Tokyo
    ```

4. 現在のコンテナの状態を`java21`という名前のイメージとして保存します：

    ```bash
    docker commit <container_id> java21
    ```

5. Ubuntu のコンテナを削除します：

    ```bash
    docker rm -f ubuntu
    ```

6. `java21`イメージから新しいコンテナを起動します：

    ```bash
    docker run -it java21 bash
    ```

7. `wget`をインストールします：

    ```bash
    apt install wget
    ```

8. Minecraft サーバーの jar ファイルをダウンロードします：

    ```bash
    wget https://piston-data.mojang.com/v1/objects/8dd1a28015f51b1803213892b50b7b4fc76e594d/server.jar
    ```

9. Minecraft サーバーを起動します：

    ```bash
    java -Xmx2G -Xms2G -jar server.jar nogui
    ```

10. EULA を確認します：

    ```bash
    cat eula.txt
    ```

11. EULA を承諾します：

    ```bash
    sudo sed -i 's/eula=false/eula=true/g' eula.txt
    ```

12. 現在のコンテナの状態を`minecraft`という名前のイメージとして保存します：

    ```bash
    docker commit <container_id> minecraft
    ```

13. `java21`のコンテナを削除します：

    ```bash
    docker rm -f java21
    ```

14. `minecraft`イメージから新しいコンテナを起動し、ポート 25565 をマッピングします：

    ```bash
    docker run -itp 25565:25565 --name sugukesu minecraft bash
    ```

15. Minecraft サーバーを再度起動します：
    ```bash
    java -Xmx2G -Xms2G -jar server.jar nogui
    ```

以上の手順で、Minecraft サーバーがセットアップされます。
