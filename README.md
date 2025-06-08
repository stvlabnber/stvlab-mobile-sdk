# stvlab-mobile-lib

## 此 aar 檔包含 android app 開發上可使用的共用元件，包含以下 package:
1. network: SSL 憑證綁定驗證, SSL 伺服器端憑證驗證
2. util: 通知功能處理, 網路上傳下載資料處理, DialogHelper, ImageViewHelper
3. view: 九宮格、行事曆、ViewPager


## 使用說明:

### 1.SSL 憑證綁定驗證
SSLHelper.initCheckCert(true);
SSLHelper.initCertPinning("test.crt");
SSLHelper.initServerTrusted("xxxxx");//cert sha256 public key
SSLHelper.validate(context, httpsConn);//SSL 憑證驗證


### 2.九宮格
DragGridView grid = new DragGridView(context);//create grid view
grid.setFooterTextSize(13f);
List<GridItem> list = new ArrayList<GridItem>();
list.add(new GridItem("1", R.mipmap.news, "news", 0));
list.add(new GridItem("2", R.mipmap.stock, "stock", 1));
list.add(new GridItem("3", R.mipmap.market, "market", 2));

GridHelper.init("test");//sharedPreference file name
GridHelper.showFooterText(true);
GridHelper.setDraggable(true);
GridHelper.load(context, grid, list);

grid.setOnRearrangeListener(new DragGridView.OnRearrangeListener() {
	public void onRearrange(int oldIndex, int newIndex) {
		GridHelper.reorderGridItems(context, list, oldIndex, newIndex);
	}
});

grid.setOnItemClickListener(new OnItemClickListener() {
	@Override
	public void onItemClick(AdapterView<?> parent, View view, int position, long arg3) {
		GridItem gridItem = (GridItem) view.getTag();
		FuncController.startActivity(context, gridItem.key, null);
	}
});

