# Skip To Page
   > Old
   ```js
       for (let [i, page] of manifest.page.entries()) {...};
   ```
   > New
   - Downloads pages starting at page **<span style="color: orange">X</span>**, in case download is interrupted, you won't have to redownload every page from the beginning.
   - **default value = <span style="color: orange">0</span>**
   ```js
       for (let [i, page] of manifest.page.splice(X).entries()) {...};
   ```
---
# Timer - Random Number
   > Old
   ```js
       await sleep(GOOGLE_PAGE_DOWNLOAD_PACER); // Be gentle with Google Play Books
   ```
   > New
   - Generates a random number between **<span style="color: orange">MIN</span>** to **<span style="color: orange">MAX</span>**.
   - **Recommended values = <span style="color: orange">MIN</span> > 1000**, **<span style="color: orange">MAX</span> < 10000** milliseconds to not get flagged immediately.
   ```js
       let randomNumber = (min, max) => (Math.random() * (max - min + 1) + min);
   
       await sleep(randomNumber(MIN,MAX)); 
```

---
# Rework - Copy as Node.js fetch
   > Old
   ```js
   ```
   > New
   - dummy-proofing the copy & paste process
   ```js
    const promise1 = new Promise((resolve, reject) => {
        resolve(
            `fetch(...)`
        );
    });

    promise1.then((value) => console.log(value.replace(/^fetch\(|(?<=\})\)(?=;)$/,'')));
   ```

---
# Rework - Encoding Errors
   > Old
   ```js
        with open(f'{base_path}/manifest.json') as f_manifest:
   ```
   > New
   - Fixes metadata being written incorrectly (e.g., 'ド' (`U+30C9`) being read as '0É' (`U+0030` & `U+00C9`), etc.).
   - **default value = <span style="color: orange">utf-8</span>**.
   ```js
        with open(f'{base_path}/manifest.json', encoding='utf-8') as f_manifest:
   ```

---
# Rework - Overwriting Errors
   > Old
   ```js
    fs.writeFile('pages.txt', page_files.join('\n'));
   ```
   > New
   - Prevents overwriting / deleting pages, if the download is interrupted and restarted.
   - TODO - Check for duplicate entries.
   ```js
    fs.appendFile('pages.txt', page_files.join('\n'));
   ```

---
# Template
   > Old
   ```js
   ```
   > New
   ```js
   ```

---
# Template
   > Old
   ```js
   ```
   > New
   ```js
   ```