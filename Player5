<?php
$broadcast1Page = 'https://hd.yallashoot-live.today/albaplayer/bein-max-1/?serv=1';
$broadcast2Page = 'https://hd.yallashoot-live.today/albaplayer/bein-max-1/?serv=2';
$playerSource = 'https://www.youtube.com/embed/5VtrmK81NG4';
$telegramChannel = 'https://t.me/TimeMatche';

function e($value) {
  return htmlspecialchars($value, ENT_QUOTES, 'UTF-8');
}
?>
<!DOCTYPE html>
<html dir="rtl" lang="ar">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta name="referrer" content="no-referrer" />
  <title>bein max 1</title>

  <style>
    :root {
      --main-color: #0c1889;
      --active-color: #911e1e;
      --background: #000;
      --text-color: #fff;
    }

    * {
      box-sizing: border-box;
      text-decoration: none;
    }

    html,
    body {
      width: 100%;
      height: 100%;
      margin: 0;
      background: var(--background);
      color: var(--text-color);
      font-family: Arial, sans-serif;
    }

    body {
      overflow: hidden;
    }

    /* شريط أزرار البث */
    .broadcast-bar {
      width: 100%;
      display: flex;
      gap: 4px;
      padding: 4px;
      background: #000;
      direction: rtl;
    }

    .broadcast-bar a {
      flex: 1;
      min-width: 0;
      height: 42px;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 5px;
      border-radius: 2px;
      background: var(--main-color);
      color: #fff;
      font-size: 16px;
      font-weight: 700;
      text-shadow: 0 1px 1px rgba(0, 0, 0, .35);
      transition: background .2s ease;
    }

    .broadcast-bar a:hover,
    .broadcast-bar a.active {
      background: var(--active-color);
    }

    /* أزرار التحديث والمشاركة فوق المشغل */
    .player-actions {
      position: absolute;
      z-index: 20;
      top: 8px;
      right: 8px;
      left: 8px;
      height: 32px;
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      pointer-events: none;
    }

    .action-button {
      pointer-events: auto;
      border: 0;
      border-radius: 3px;
      padding: 6px 12px;
      background: var(--active-color);
      color: #fff;
      cursor: pointer;
      font-size: 14px;
      font-weight: 700;
      font-family: Arial, sans-serif;
      box-shadow: 0 1px 3px rgba(0, 0, 0, .45);
    }

    .action-button:hover {
      background: #b72a2a;
    }

    .player-wrapper {
      position: relative;
      width: 100%;
      height: calc(100vh - 50px);
      min-height: 250px;
      overflow: hidden;
      background: #000;
    }

    .video-container {
      position: relative;
      width: 100%;
      height: 100%;
      overflow: hidden;
      background: #000;
    }

    .video-container iframe {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      border: 0;
    }

    /* نافذة المشاركة */
    .share-overlay {
      position: fixed;
      z-index: 100;
      inset: 0;
      display: none;
      align-items: center;
      justify-content: center;
      padding: 15px;
      background: rgba(0, 0, 0, .9);
    }

    .share-overlay.open {
      display: flex;
    }

    .share-box {
      width: min(600px, 100%);
      padding: 20px;
      border-radius: 6px;
      background: #171717;
      text-align: center;
    }

    .share-box h3 {
      margin: 0 0 12px;
      color: #fff;
      font-size: 20px;
    }

    .share-box textarea {
      width: 100%;
      height: 72px;
      resize: none;
      direction: ltr;
      padding: 8px;
      border: 1px solid #444;
      border-radius: 4px;
      background: #292929;
      color: #fff;
      font-size: 13px;
    }

    .share-buttons {
      display: flex;
      justify-content: center;
      gap: 8px;
      margin-top: 10px;
    }

    .share-buttons button {
      border: 0;
      border-radius: 4px;
      padding: 8px 18px;
      color: #fff;
      background: var(--main-color);
      cursor: pointer;
      font-size: 14px;
      font-weight: 700;
    }

    .share-buttons button.close {
      background: #555;
    }

    /* نافذة تيليجرام الصغيرة المنبثقة */
    .telegram-float {
      position: fixed;
      z-index: 90;
      right: 18px;
      bottom: 18px;
      width: min(310px, calc(100% - 36px));
      padding: 24px 16px 16px;
      border: 1px solid rgba(255, 255, 255, .18);
      border-radius: 10px;
      background: linear-gradient(145deg, #168acd, #0c6fa9);
      color: #fff;
      box-shadow: 0 5px 20px rgba(0, 0, 0, .65);
      direction: rtl;
      text-align: center;
      animation: telegramPopup .35s ease-out;
    }

    @keyframes telegramPopup {
      from {
        opacity: 0;
        transform: translateY(18px) scale(.94);
      }
      to {
        opacity: 1;
        transform: translateY(0) scale(1);
      }
    }

    .telegram-float strong {
      display: block;
      color: #fff;
      font-size: 15px;
      line-height: 1.6;
    }

    .telegram-float small {
      display: block;
      margin-top: 5px;
      color: rgba(255, 255, 255, .9);
      font-size: 12px;
    }

    .telegram-icon {
      width: 38px;
      height: 38px;
      margin-bottom: 7px;
      fill: #fff;
    }

    .telegram-join {
      display: block;
      margin-top: 13px;
      padding: 9px 12px;
      border-radius: 5px;
      background: #fff;
      color: #0c6fa9;
      font-size: 14px;
      font-weight: 700;
      transition: background .2s ease, color .2s ease;
    }

    .telegram-join:hover {
      background: #e9f7ff;
      color: #07547f;
    }

    .telegram-close {
      position: absolute;
      top: 7px;
      left: 7px;
      width: 23px;
      height: 23px;
      padding: 0;
      border: 0;
      border-radius: 50%;
      background: rgba(0, 0, 0, .35);
      color: #fff;
      cursor: pointer;
      font-size: 16px;
      font-weight: 700;
      line-height: 21px;
    }

    .telegram-close:hover {
      background: rgba(0, 0, 0, .6);
    }

    @media (max-width: 640px) {
      .broadcast-bar a {
        height: 32px;
        font-size: 14px;
      }

      .player-wrapper {
        height: calc(100vh - 40px);
      }

      .action-button {
        padding: 5px 9px;
        font-size: 12px;
      }
    }
  </style>
</head>

<body>
  <!-- البث 1 والبث 2 -->
  <nav class="broadcast-bar" aria-label="اختيار البث">
    <a
      class="active"
      href="<?= e($broadcast1Page) ?>"
      title="فتح البث 1">
      البث 1
    </a>

    <a
      href="<?= e($broadcast2Page) ?>"
      title="فتح البث 2">
      البث 2
    </a>
  </nav>

  <main class="player-wrapper">
    <!-- زر التحديث وزر المشاركة -->
    <div class="player-actions">
      <button class="action-button" type="button" onclick="reloadPlayer()" title="تحديث البث">
        ↻ تحديث
      </button>

      <button class="action-button" type="button" onclick="openShare()" title="مشاركة المشغل">
        مشاركة ↗
      </button>
    </div>

    <div class="video-container">
      <!-- رابط الفيديو الحالي الموجود في الملف الأصلي -->
      <iframe
        src="<?= e($playerSource) ?>"
        allow="autoplay; encrypted-media; picture-in-picture; fullscreen"
        allowfullscreen
        scrolling="no"
        title="مشغل البث">
      </iframe>
    </div>
  </main>

  <!-- نافذة منبثقة صغيرة لقناة التليجرام -->
  <div id="telegramFloat" class="telegram-float" role="dialog" aria-label="قناة التليجرام">
    <button class="telegram-close" type="button" aria-label="إغلاق" title="إغلاق" onclick="closeTelegramFloat(event)">×</button>

    <svg class="telegram-icon" viewBox="0 0 24 24" aria-hidden="true">
      <path d="M21.5 3.5 18.2 20c-.25 1.17-.9 1.46-1.83.91l-5.04-3.72-2.43 2.34c-.27.27-.5.5-1.02.5l.36-5.13 9.34-8.44c.41-.36-.09-.56-.64-.2L5.39 13.58.42 12.02c-1.08-.34-1.1-1.08.23-1.58L20.08 2.9c.9-.33 1.68.2 1.42.6Z"></path>
    </svg>

    <strong>لمشاهدة جميع المباريات انضم لقناة التليجرام</strong>
    <small>تابع مواعيد المباريات والبث المباشر</small>

    <a class="telegram-join" href="<?= e($telegramChannel) ?>" target="_blank" rel="noopener noreferrer nofollow">
      انضم إلى القناة الآن
    </a>
  </div>

  <!-- نافذة المشاركة -->
  <div id="shareOverlay" class="share-overlay" role="dialog" aria-modal="true" aria-label="مشاركة المشغل">
    <div class="share-box">
      <h3>كود تضمين المشغل</h3>

      <textarea id="embedCode" readonly onclick="this.select()"></textarea>

      <div class="share-buttons">
        <button type="button" onclick="copyEmbedCode()">نسخ الكود</button>
        <button class="close" type="button" onclick="closeShare()">إغلاق</button>
      </div>
    </div>
  </div>

  <script>
    function reloadPlayer() {
      window.location.reload();
    }

    function openShare() {
      const pageUrl = window.location.href.split('#')[0];
      const embedCode = '<iframe allowfullscreen="true" frameborder="0" height="500px" scrolling="no" src="' + pageUrl + '" width="100%"></iframe>';

      document.getElementById('embedCode').value = embedCode;
      document.getElementById('shareOverlay').classList.add('open');
    }

    function closeShare() {
      document.getElementById('shareOverlay').classList.remove('open');
    }

    function closeTelegramFloat(event) {
      event.preventDefault();
      event.stopPropagation();
      document.getElementById('telegramFloat').style.display = 'none';
    }

    function copyEmbedCode() {
      const textarea = document.getElementById('embedCode');
      textarea.select();
      textarea.setSelectionRange(0, 99999);

      if (navigator.clipboard && window.isSecureContext) {
        navigator.clipboard.writeText(textarea.value).then(function() {
          alert('تم نسخ كود التضمين');
        });
      } else {
        document.execCommand('copy');
        alert('تم نسخ كود التضمين');
      }
    }

    document.getElementById('shareOverlay').addEventListener('click', function(event) {
      if (event.target === this) {
        closeShare();
      }
    });
  </script>
</body>
</html>
