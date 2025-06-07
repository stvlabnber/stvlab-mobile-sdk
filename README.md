# stvlab-mobile-lib

## 此 aar 檔包含 android app 開發上可使用的共用元件，包含以下 package:
1. network: SSL 憑證綁定驗證, SSL 伺服器端憑證驗證
2. util: 通知功能處理, 網路上傳下載資料處理, DialogHelper, ImageViewHelper
3. view: 九宮格、行事曆、ViewPager


## 使用說明:

### 1.SSL 憑證綁定驗證
SSLHelper.initCheckCert(true);

SSLHelper.initCertPinning(true, "xxx.crt");

SSLHelper.initServerTrusted(true, "xxxxx");//cert sha256 public key

SSLHelper.setSocketFactory(context, httpsConn);//SSL 憑證驗證


### 2.九宮格: 
DragGridView grid = new DragGridView(context);//create grid view
grid.setFooterTextSize(13f);
list = FuncController.getGridItems(context);//預設清單
GridHelper.init(context, grid, list, true, false, true, prefFileName);


