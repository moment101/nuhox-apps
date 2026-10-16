# docs — 要放到網路上的頁面

App Store Connect 的「隱私政策網址」是**必填**欄位，空的就送不出去；
訂閱的付費牆上也必須有可用的連結（指南 3.1.2）。這個資料夾就是為了那個網址。

## 發布（約兩分鐘）

GitHub Pages 免費而且夠用：

```bash
cd "products/docs"
git init && git add -A && git commit -m "隱私政策"
gh repo create nuhox-apps --public --source=. --push
```

然後到 repo 的 Settings → Pages，Source 選 `main` 分支的根目錄，存檔。
一兩分鐘後網址會是：

```
https://<你的帳號>.github.io/nuhox-apps/pitchcoach/privacy.html
https://<你的帳號>.github.io/nuhox-apps/breathpacer/privacy.html
```

## 發布完要改三個地方

1. `PitchCoach/PitchCoach/AppLinks.swift` 的 `privacyPolicy`
2. `BreathPacer/BreathPacer/AppLinks.swift` 的 `privacyPolicy`
3. App Store Connect 兩個 App 的「隱私政策網址」欄位

改完跑 `python3 tools/preflight.py`，那兩個 ⚠️ 會變成 ✅。

## 聯絡信箱

兩份政策裡的 `TODO@example.com` 要換成真的信箱 ——
隱私政策需要一個聯絡方式，而這個網址是公開的，所以用哪個信箱是你的決定。
HTML 與 Markdown 兩邊都要改（`docs/*/privacy.html` 和 `*/隱私政策.md`）。
