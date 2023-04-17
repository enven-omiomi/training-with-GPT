次のお願いとして、以下の3つのお題を提案します。

1. フォームの作成
2. モーダルウィンドウの実装
3. スムーズスクロールの実装

### 1. フォームの作成

ウェブサイトでユーザーから情報を収集するために、フォームを使用することが一般的です。以下に、お問い合わせフォームの例を示します。

```html
<!DOCTYPE html>
<html lang="ja-JP">
<head>
  <meta charset="utf-8">
  <title>my web page</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <!-- 既存のコンテンツ -->

  <section id="contact-form">
    <h2>お問い合わせ</h2>
    <form action="/submit" method="post">
      <label for="name">お名前：</label>
      <input type="text" id="name" name="name" required>
      <br>
      <label for="email">メールアドレス：</label>
      <input type="email" id="email" name="email" required>
      <br>
      <label for="message">お問い合わせ内容：</label>
      <textarea id="message" name="message" required></textarea>
      <br>
      <input type="submit" value="送信">
    </form>
  </section>
</body>
</html>
```

### 2. モーダルウィンドウの実装

モーダルウィンドウは、コンテンツをポップアップ表示する方法です。以下に、モーダルウィンドウを使用してお問い合わせフォームを表示する例を示します。JavaScriptを使用して、モーダルウィンドウを開いたり閉じたりします。

```html
<!DOCTYPE html>
<html lang="ja-JP">
<head>
  <meta charset="utf-8">
  <title>my web page</title>
  <link rel="stylesheet" href="styles.css">
  <script src="script.js"></script>
</head>
<body>
  <!-- 既存のコンテンツ -->

  <button id="open-modal">お問い合わせフォームを開く</button>

  <div id="modal" class="modal">
    <div class="modal-content">
      <span id="close-modal">&times;</span>
      <!-- お問い合わせフォームのコード -->
    </div>
  </div>
</body>
</html>
```

モーダルウィンドウのスタイリングには、以下のようなCSSを追加します。

```css
/* 既存のCSS */

/* モーダルウィンドウ */
.modal {
  display: none;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0,0,0,0.4);
}

.modal-content {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
}

.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}
```

JavaScriptファイル（`script.js`）を作成し、以下のコードを追加して、モーダルウィンドウの開閉を制御します。

```javascript
document.addEventListener("DOMContentLoaded", function () {
  var modal = document.getElementById("modal");
  var openModal = document.getElementById("open-modal");
  var closeModal = document.getElementById("close-modal");

  openModal.onclick = function () {
    modal.style.display = "block";
  };

  closeModal.onclick = function () {
    modal.style.display = "none";
  };

  window.onclick = function (event) {
    if (event.target == modal) {
      modal.style.display = "none";
    }
  };
});
```

### 3. スムーズスクロールの実装

スムーズスクロールは、ページ内リンクをクリックしたときに、スクロールを滑らかにアニメーションさせる機能です。以下に、スムーズスクロールを実装する例を示します。この例では、JavaScriptを使用してスクロール動作を制御しています。

まず、HTML内のページ内リンクに`data-scroll`属性を追加します。

```html
<!DOCTYPE html>
<html lang="ja-JP">
<head>
  <meta charset="utf-8">
  <title>my web page</title>
  <link rel="stylesheet" href="styles.css">
  <script src="smooth-scroll.js"></script>
</head>
<body>
  <header>
    <nav>
      <ul>
        <li><a href="#myprof" data-scroll>プロフィール</a></li>
        <li><a href="#favorite-movie" data-scroll>お気に入りの映画</a></li>
        <li><a href="#contact" data-scroll>連絡先</a></li>
      </ul>
    </nav>
  </header>
  <!-- 以降のコンテンツ -->
</body>
</html>
```

次に、`smooth-scroll.js`という新しいJavaScriptファイルを作成し、以下のコードを追加します。

```javascript
document.addEventListener("DOMContentLoaded", function () {
  var links = document.querySelectorAll("[data-scroll]");

  for (var i = 0; i < links.length; i++) {
    links[i].addEventListener("click", function (event) {
      event.preventDefault();

      var target = document.querySelector(this.getAttribute("href"));
      target.scrollIntoView({ behavior: "smooth" });
    });
  }
});
```

これで、ページ内リンクをクリックすると、スムーズスクロールが実装されます。

これらのお題に取り組むことで、フォームの作成やモーダルウィンドウ、スムーズスクロールなどの実装が身につきます。また、さらにスキルを向上させたい場合は、以下のような機能を追加してみてください。

1. アコーディオンメニュー
2. パララックス効果
3. スライダー（カルーセル）

### 1. アコーディオンメニュー

アコーディオンメニューは、クリックするとコンテンツが表示される折りたたみ式のメニューです。以下に、アコーディオンメニューを実装する例を示します。この例では、JavaScriptを使用してアコーディオンの開閉を制御しています。

```html
<!DOCTYPE html>
<html lang="ja-JP">
<head>
  <meta charset="utf-8">
  <title>my web page</title>
  <link rel="stylesheet" href="styles.css">
  <script src="accordion.js"></script>
</head>
<body>
  <!-- 既存のコンテンツ -->

  <section id="accordion">
    <button class="accordion-button">セクション1</button>
    <div class="accordion-content">
      <p>ここにセクション1の内容が入ります。</p>
    </div>

    <button class="accordion-button">セクション2</button>
    <div class="accordion-content">
      <p>ここにセクション2の内容が入ります。</p>
    </div>

    <!-- その他のセクション -->
  </section>
</body>
</html>
```

`accordion.js`ファイルを作成し、以下のコードを追加して、アコーディオンの開閉を制御します。

```javascript
document.addEventListener("DOMContentLoaded", function () {
  var acc = document.getElementsByClassName("accordion-button");

  for (var i = 0; i < acc.length; i++) {
    acc[i].addEventListener("click", function () {
      this.classList.toggle("active");
      var panel = this.nextElementSibling;
      panel.style.display = panel.style.display === "block" ? "none" : "block";
    });
  }
});
```

### 2. パララックス効果

パララックス効果は、スクロール時に背景画像がコンテンツよりもゆっくり動くことで、奥行き感を作り出す効果です。CSSの`background-attachment`プロパティを使用して、パララックス効果を実現できます。

```html
<!DOCTYPE html>
<html lang="ja-JP">
<head>
  <meta charset="utf-8">
  <title>my web page</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <!-- 既存のコンテンツ -->

  <section class="parallax">
    <div class="parallax-content">
      <h2>パララックス効果のデモ</h2>
      <p>ここにコンテンツが入ります。</p>
    </div>
  </section>
</body
