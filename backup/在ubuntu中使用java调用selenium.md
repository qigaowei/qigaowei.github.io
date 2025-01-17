1. 安装 Chrome
```shell
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
# 检查版本
google-chrome --version
```
2. 无法安装使用
```shell
sudo apt-get install -f
```
3. 安装chromedriver 
```shell
unzip chromedriver_linux64.zip
sudo mv -f chromedriver /usr/local/share/chromedriver
sudo ln -s /usr/local/share/chromedriver /usr/local/bin/chromedriver
sudo ln -s /usr/local/share/chromedriver /usr/bin/chromedriver
chromedriver --version
```
4. java配置
```java
options.setBinary("/opt/google/chrome/chrome");
 System.setProperty("webdriver.chrome.driver", "/usr/local/share/chromedriver");
options.addArguments("--headless"); //使用无头模式
options.addArguments("--disable-javascript");
```

参考网站
- https://blog.csdn.net/weixin_44184990/article/details/123590435

