
# 🚀 GitHub Uploader API

> **A lightweight Node.js module to automatically upload files (images, videos, audios, documents, etc.) to a GitHub repository via REST API.**
> Built for seamless integration with bots and automation systems.

---

## 📦 Features

| Feature | Description |
|----------|--------------|
| ⚡ **Auto Categorization** | Automatically organizes files into folders (`image/`, `video/`, `audio/`, `sticker/`). |
| 🔒 **Secure Token Auth** | Uses GitHub Personal Access Token (Classic) with repo content permissions. |
| 🧠 **Smart MIME Detection** | Handles common MIME types for cleaner file extensions. |
| 💾 **Instant Raw Links** | Returns direct `raw.githubusercontent.com` links for easy media access. |
| 🪶 **Lightweight** | No external dependencies except Axios and Chalk. |

---

## ⚙️ Installation

```bash
npm install axios chalk
```

Then include the uploader script:

```js
const gitUploader = require('./gitUploader');
```

---

## 🚀 Usage Example

```js
const fs = require('fs');
const gitUploader = require('./gitUploader');

(async () => {
  const buffer = fs.readFileSync('./image.jpg');
  const result = await gitUploader(buffer, 'test_upload', 'image/jpeg');
  console.log(result);
})();
```

**Output Example:**
```js
{
  status: true,
  url: "https://raw.githubusercontent.com/username/repo/main/image/test_upload.jpg",
  path: "image/test_upload.jpg",
  type: "image",
  mime: "image/jpeg"
}
```

---

## 🔐 Token Permissions

When creating your **GitHub Personal Access Token (Classic)**, enable only:

| Permission | Access Type | Required |
|-------------|--------------|----------|
| **Contents** | Read and Write | ✅ |
| **Metadata** | Read-only | ✅ |

> 💡 Avoid enabling **“repo creation”** permission to reduce security risks.

---

## 📁 Folder Structure

```
📦 uploader
 ┣ 📂 image
 ┣ 📂 video
 ┣ 📂 audio
 ┣ 📂 sticker
 ┣ 📜 gitUploader.js
 ┗ 📜 README.md
```

---

## 🧩 Error Handling

The uploader will return a structured error if something goes wrong:

```js
{
  status: false,
  error: "Repository not found"
}
```

> If your repository doesn’t exist, simply create one manually named **“uploader”** under your GitHub account.

---

## 🧑‍💻 Developer Info

| Field | Detail |
|--------|--------|
| **Author** | [Maxz](https://linktr.ee/dcodemaxz) |
| **Project** | Vikaru-Bot Uploader System |
| **Language** | Node.js (ES6) |
| **License** | MIT |

---

## 🖋️ Notes

- Tested on **Node.js v20+**
- Designed for **Baileys-based bots**
- Clean, modular, and easy to integrate

---

⭐ **If you like this project, don’t forget to star the repo!**
