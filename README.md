
# `react-native` 如何使用 `code-push` 熱更新

## 使用前須知

 - Q: “蘋果應用商店和android應用商店允不允許使用熱更新？”    
   A: “都允許。”

   > 蘋果允許使用熱更新[Apple's developer agreement](https://developer.apple.com/programs/ios/information/iOS_Program_Information_4_3_15.pdf), 但是規定不能彈框提示用戶更新，影響用戶體驗。 
   > Google Play也允許熱更新，但必須彈框告知用戶更新。在中國的android市場發佈時，都必須關閉更新彈框，否則會在審核應用時以“請上傳最新版本的二進制應用包”駁回應用。 


 - Q: “為什麼推薦code-push？”    
   A: ”非常好。除了滿足基本更新功能外，還有統計，hash計算容錯和補丁更新功能。微軟的項目，大公司技術有保障，而且開源。近幾年微軟在擁抱開源方面，讓大家也是刮目相看。“

## 安裝

code-push-server 

npm install code-push-server -g 

Install mysql:https://ken.io/note/macos-mysql8-install-config-tutorial

服務權限打開(這樣不用每次都打密碼)
sudo chmod 777 /usr/local/mysql/support-files/mysql.server 
環境變數設定
open ~/.bash_profile 
PATH=$PATH:/usr/local/mysql/bin
source ~/.bash_profile

root設定權限:
mysql -uroot -p
ALTER USER `root`@`localhost` IDENTIFIED WITH mysql_native_password BY `password`; (直接複製貼上改密碼) flush privileges; 初始化資料庫 
code-push-server yanyuyuan$ code-push-server-db init --dbhost localhost --dbuser root --dbpassword 12345678  設定 code-push-server config.js

 open /usr/local/lib/node_modules/code-push-server/config/config.js
要改的地方
db :info
Local : storageDir,downloadUrl

Start Server
Code-push-server
拿token 127.0.0.1:3000  user:admin password:123456

code-push login 
輸入token
Server設定完成！！！


