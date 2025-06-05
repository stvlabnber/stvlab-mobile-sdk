# stvlab-mobile-lib
## 此 aar 檔包含 android app 開發上可使用的共用元件，包含以下 package:
1. network: ssl 憑證綁定驗證, ssl 伺服器端憑證驗證
2. util: ActivityHelper, ActivityManagerDeviceHelper, DialogHelper, ImageViewHelper
3. view: 九宮格、行事曆、ViewPager


## 使用說明:

### 1.ssl 憑證綁定驗證
SslHelper.initCheckCert(true);

SslHelper.initCertPinning(true, "xxx.crt");

SslHelper.initServerTrusted(true, "xxxxx");//cert sha256 public key

SslHelper.setSocketFactory(context, httpsConn);//ssl 憑證驗證


### 2.九宮格: 

待補充。


