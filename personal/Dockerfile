# コンテナ内のみの作業でマイクラ鯖を建てる
# $ docker run -it ubuntu bash
# $ apt install openjdk-21-jre
# apt install tzdata
# timedatectl set-timezone Asia/Tokyo
# docker commit <container_id> java21 いったんイメージを作る
# docker rm -f ubuntu
# docker run -it java21 bash
# apt install wget
# wget https://piston-data.mojang.com/v1/objects/8dd1a28015f51b1803213892b50b7b4fc76e594d/server.jar
# java -Xmx2G -Xms2G -jar server.jar nogui
# cat eula.txt
# sudo sed -i 's/eula=false/eula=true/g' eula.txt
# docekr commit <container_id> minecraft いったんイメージを作る
# docker rm -f java21
# docker run -itp 25565:25565 --name sugukesu minecraft bash
# java -Xmx2G -Xms2G -jar server.jar nogui
# これでマイクラ鯖が建てられる