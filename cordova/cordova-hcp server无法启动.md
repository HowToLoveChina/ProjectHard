***
cordova-hcp server 蓋因ngrok無法運作，致此命令無法正常執行
***
夫用nvm者，可修訂

 '''.nvm/v8.11.3/lib/node_modules/cordova-hot-code-push-cli/src/server.js '''
 於行184，將如下代碼刪去
>        ngrok.connect(port, function (err, url) {
>          if (err) {
>            publicTunnelDfd.reject(err);
>            return console.log('Could not create tunnel: ', err);
>          }
>          updateLocalEnv({content_url: url});
>          publicTunnelDfd.resolve(url);
>        });

替換爲

>        url = "http://noexist.com:6666";
>         updateLocalEnv({content_url: url});
>         publicTunnelDfd.resolve(url);

關於上級目錄 npm rebuild 
***
即可修復本異常 
