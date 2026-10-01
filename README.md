# Zen Trading Cover Generator

A standalone browser tool for creating Zen Trading daily cover images. It is designed for the team workflow where an AI Bot prepares the article content and a colleague generates the final cover before publishing.

## Files

- `index.html` — the complete generator. It includes the Zen Trading logo, brand font, and visual styles, so it can run without an asset folder.
- `README.md` — setup and usage notes.

## Features

- Wide cover format: 900 × 383 px
- Square cover format: 900 × 900 px
- Centered logo, date, headline, keywords, and English tags
- Official Zen Trading logo and Montserrat font embedded in the HTML
- Temporary logo replacement with a reset button
- PNG download directly from the browser
- Paste a WeChat article title and automatically detect the ISO date and headline keywords
- Import an AI Bot JSON object to fill the cover fields without a second guess
- All processing happens locally in the browser; no API key or build step is required

## Run locally

1. Open `index.html` in Chrome, Safari, or Edge.
2. Choose the cover format.
3. Fill in the date, section, cover keywords, and English tags.
4. Click **生成封面** and then download the PNG.

The tool works by double-clicking the file. It does not require Node.js, Python, a server, or an internet connection.

## Use a WeChat article title

Paste a complete title into **粘贴公众号文章标题**, then click **解析标题**. For example:

```text
美债收益率创02年以来新高 软件股逆势支撑美股（日更·2026-10-01）
```

The parser extracts a date in `YYYY-MM-DD` format and splits the remaining text into candidate cover keywords. Because this is a deterministic browser parser rather than an AI model, review the extracted wording before downloading.

## Import AI Bot JSON

The most reliable workflow is to have the AI Bot output the cover fields in JSON, then paste the JSON into **导入 AI Bot JSON**:

```json
{
  "publish_date": "2026-10-01",
  "section": "开市日报 · DAILY BRIEF",
  "cover_keywords": [
    "美债收益率新高",
    "软件股逆势支撑",
    "美股"
  ],
  "english_tags": [
    "US TREASURY YIELDS",
    "SOFTWARE STOCKS",
    "US EQUITIES"
  ]
}
```

The importer accepts common aliases such as `date`, `title`, `keywords`, `tags`, and `englishTags`. After importing, check the preview and make any editorial adjustments before exporting the PNG.

## Publish with GitHub Pages

1. Create or open a GitHub repository.
2. Upload `index.html` to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, select `main`, and choose `/ (root)`.
5. Save and open the generated Pages URL.

The same `index.html` can be opened locally or hosted as a simple static GitHub Pages site.

## Suggested AI Bot output contract

Ask the Bot to return these fields so the cover generator and the WeChat article stay aligned:

```text
publish_date      ISO date, YYYY-MM-DD
section           short Chinese section name plus optional English label
cover_keywords   2–4 concise Chinese phrases for the cover
english_tags      2–4 uppercase English tags
```

The generator only creates the image. The final article review and WeChat publishing step should still be handled by a person.

## Brand note

The current design follows the existing Zen Trading visual system: dark navy background, centered typography, embedded Zen Trading logo, and the existing Montserrat brand font. If the official brand assets are updated later, replace the embedded assets in the source HTML and regenerate the ZIP.

