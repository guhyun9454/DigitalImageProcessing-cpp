### 📝 Code Snippet

```cpp
void CMainDialog::OnExample2(wxCommandEvent& event) {
	//마지막 선택된 이미지
	CKcImage kcImage = GetLastSelImage(0);
	if (kcImage.cvImage.empty()) return;
	cv::Mat img = kcImage.cvImage.clone();
	cv::Mat rot = cv::getRotationMatrix2D(cv::Point2f(img.cols / 2, img.rows / 2), 45, 1);

	for (int i = 0; i < 1000; i++) {
		cv::warpAffine(img, img, rot, img.size());
	}

	DisplayImage(img, kcImage.pos.x, kcImage.pos.y, true, false);
}
```

### 📷 Output Image

![](./images/1.jpg)

> 1000번 돌려서 흐릿해짐

-------