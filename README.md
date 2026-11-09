# Yu-Han Huang — 個人網站（al-folio）

網址：https://estherhan1.github.io/web/

這個網站用 [al-folio](https://github.com/alshedivat/al-folio) 模板（Jekyll）。你只要改內容檔案（Markdown / YAML / BibTeX），push 到 `main` 之後，GitHub Actions 會自動 build，並把產生的網站推到 `gh-pages` 分支。

## 要改什麼，就改哪個檔案

| 想改的東西 | 檔案 |
| --- | --- |
| 名字、網址、全站設定、作者粗體（`scholar:` 區塊） | `_config.yml` |
| 首頁自我介紹、研究經歷、實習 | `_pages/about.md` |
| 大頭照 | 把照片放到 `assets/img/prof_pic.jpg`，再把 `_pages/about.md` 裡的 `image:` 改成 `prof_pic.jpg` |
| News | `_news/` 裡一則一個檔案（照 `announcement_4.md` 的格式複製一份，改 `date:` 和內容） |
| News 日期顯示格式（目前 `Nov 2026`） | `_includes/news.liquid` 裡的 `date: '%b %Y'`（這是覆蓋 al-folio 模板的本地版本） |
| 論文 | `_bibliography/papers.bib`（BibTeX） |
| 首頁最下面的 Awards / Skills | `_data/awards.yml` / `_data/skills.yml` |
| 論文縮圖 | `assets/img/publication_preview/`，在 bib 寫 `preview = {檔名}` |
| 課程專案 | `_projects/` 裡一個專案一個檔案，圖片放 `assets/img/projects/`，`pdf:` 欄位是 PDF 按鈕的連結 |
| CV 頁面 | 已刪除，`/cv/` 會直接轉到 PDF |
| CV PDF | 直接換掉根目錄的 `CV.pdf`（導覽列的 cv 會直接開這個 PDF，設定在 `_pages/cv.html` 的 `nav_link:`） |
| 社群連結（Email、GitHub、LinkedIn、Scholar） | `_data/socials.yml` |
| 導覽列順序 | 各 `_pages/*.md` 開頭的 `nav_order:` |

### papers.bib 常用欄位

```bibtex
@inproceedings{key,
  abbr      = {SLT},                 % 左邊的會議徽章
  title     = {...},
  author    = {Huang, Yu-Han and Yang*, Chih-Kai},   % * = equal contribution
  booktitle = {...},
  year      = {2026},
  note      = {Accepted},
  arxiv     = {2607.11801},          % 產生 arXiv 按鈕
  doi       = {10.21437/...},         % 產生 DOI 按鈕
  website   = {https://...},          % 產生 Website 按鈕
  code      = {https://github.com/...}, % 產生 Code 按鈕
  preview   = {iaan.webp},            % 縮圖
  selected  = {true}                  % 顯示在首頁 selected publications
}
```

你的名字會自動加底線，因為 `_config.yml` 裡的 `scholar.last_name` / `first_name` 設成了 Huang / Yu-Han。

## 本機預覽

需要 Ruby 3 以上（macOS 內建的 2.6 太舊）：

```bash
brew install ruby imagemagick
export PATH=/opt/homebrew/opt/ruby/bin:$PATH
bundle config set --local path vendor/bundle
bundle install
bundle exec jekyll serve
```

打開 http://localhost:4000/web/ （注意網址結尾的 `/web/`）。改 Markdown 會自動重新整理；改 `_config.yml` 要重開 `jekyll serve`。

## 發布

```bash
git add -A
git commit -m "Update news"
git push
```

push 後到 repo 的 **Actions** 分頁看 “Deploy site” 有沒有跑成功（約 3–5 分鐘）。

第一次設定（只需做一次）：GitHub repo → **Settings → Pages → Build and deployment**，Source 選 **Deploy from a branch**，Branch 選 **`gh-pages`** / `/ (root)`。

## 進一步的文件

- al-folio 官方客製化說明：https://github.com/alshedivat/al-folio/blob/main/docs/CUSTOMIZE.md
- 常見問題：https://github.com/alshedivat/al-folio/blob/main/docs/FAQ.md
