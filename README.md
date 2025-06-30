# stvlab-mobile-lib

## 此 aar 檔包含 android app 開發上可使用的共用元件，包含以下 package:
1. network: SSL 憑證綁定驗證, SSL 伺服器端憑證驗證
2. util: 通知功能處理, 網路上傳下載資料處理, DialogHelper, ImageViewHelper
3. view: 九宮格、行事曆、ViewPager


## 使用說明:

### 1.SSL 憑證綁定驗證
SslManager.initCheckCert(true);

SslManager.initCertPinning("test.crt");

SslManager.initServerTrusted("xxxxx");//cert sha256 public key

SslManager.validate(context, httpsConn);//SSL 憑證驗證


### 2.九宮格
GridView grid = new GridView(context);//create grid view

grid.setFooterTextSize(13f);

List<GridItem> list = new ArrayList<GridItem>();

list.add(new GridItem("1", R.mipmap.news, "news", 0));

list.add(new GridItem("2", R.mipmap.stock, "stock", 1));

list.add(new GridItem("3", R.mipmap.market, "market", 2));

GridManager.init("test");//sharedPreference file name

GridManager.showFooterText(true);

GridManager.setDraggable(true);

GridManager.load(context, grid, list);

grid.setOnRearrangeListener(new DragGridView.OnRearrangeListener() {
	public void onRearrange(int oldIndex, int newIndex) {
		GridManager.reorderGridItems(context, list, oldIndex, newIndex);
	}
});

grid.setOnItemClickListener(new OnItemClickListener() {
	@Override
	public void onItemClick(AdapterView<?> parent, View view, int position, long arg3) {
		GridItem gridItem = (GridItem) view.getTag();
		FuncController.startActivity(context, gridItem.key, null);
	}
});


### 3.檔案下載
String fileName = "form.pdf";

final String fileUrl = "https://your_file_url";

final String filePath = "your_file_path";

FileDownloader.DownloadCompleteListener downloadCompleteListener = new FileDownloader.DownloadCompleteListener() {
	@Override
	public void onDownloadComplete() {
		if(FileHelper.checkPdfValid(filePath)){
			Bundle bundle = new Bundle();
			bundle.putString(DataKey.PDF_PATH, filePath);
			bundle.putString(DataKey.PDF_TITLE, context.getResources().getString(R.string.pdf_view_title));
			ActivityHelper.startActivity(context, PdfViewActivity.class, bundle);
		}
	}
};

FileDownloader.download(context, fileUrl, filePath, downloadCompleteListener);