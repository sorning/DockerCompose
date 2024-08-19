components: python(with scrapy-splash, httpx), splash, [restapi]

sudo docker compose run scrapy scrapy myscrapy .
sudo chown -R ubuntu:ubuntu myscrapy scrapy.cfg
sudo docker compose up
(可更改command 的内容来实现命令)


scrapy-splash配置
https://github.com/scrapy-plugins/scrapy-splash

按照配置说明，配置好1-5步骤，splash_url中的IP要用服务器IP，同时在AWS中打开8050或相应端口。