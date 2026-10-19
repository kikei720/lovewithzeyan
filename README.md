# lovewithzeyan<!DOCTYPE html>
<html lang="zh">
<head>
  <meta charset="UTF-8">
  <title>×× 自定义界面</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-size: cover;
      background-position: center;
      color: #fff;
    }
    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px;
      background: rgba(0,0,0,0.5);
    }
    #timeTemp {
      font-size: 14px;
    }
    #musicBtn {
      background: #fff;
      border: none;
      border-radius: 50%;
      width: 40px;
      height: 40px;
    }
    main {
      padding: 20px;
      text-align: center;
    }
    .custom-img {
      width: 45%;
      height: 200px;
      margin: 10px;
      background: rgba(255,255,255,0.2);
      display: inline-block;
      background-size: cover;
      background-position: center;
    }
    #searchBar {
      margin-top: 20px;
    }
    #searchInput {
      width: 70%;
      padding: 8px;
    }
    #searchBtn {
      padding: 8px;
    }
    footer {
      position: fixed;
      bottom: 0;
      width: 100%;
      display: flex;
      justify-content: space-around;
      background: rgba(0,0,0,0.5);
      padding: 10px;
    }
    .widget {
      width: 50px;
      height: 50px;
      background: rgba(255,255,255,0.2);
      border-radius: 10px;
      background-size: cover;
      background-position: center;
    }
  </style>
</head>
<body>
  <header>
    <div id="timeTemp">18:33 28°</div>
    <button id="musicBtn">▶</button>
    <input type="file" id="musicUpload" accept="audio/*" style="display:none;">
    <audio id="bgMusic" controls style="display:none;"></audio>
  </header>

  <main>
    <div>
      <div id="img1" class="custom-img"></div>
      <div id="img2" class="custom-img"></div>
    </div>
    <input type="file" id="imgUpload1" accept="image/*">
    <input type="file" id="imgUpload2" accept="image/*">

    <div id="searchBar">
      <input id="searchInput" placeholder="搜索聊天记录..." />
      <button id="searchBtn">搜索</button>
    </div>
  </main>

  <footer>
    <div id="widget1" class="widget"></div>
    <div id="widget2" class="widget"></div>
    <div id="widget3" class="widget"></div>
    <div id="widget4" class="widget"></div>
  </footer>

  <input type="file" id="bgUpload" accept="image/*">

  <script>
    // 时间显示
    function updateTime() {
      const now = new Date();
      document.getElementById('timeTemp').innerText =
        now.toLocaleTimeString() + " 28°";
    }
    setInterval(updateTime, 1000);

    // 背景图片导入
    document.getElementById('bgUpload').addEventListener('change', e => {
      const file = e.target.files[0];
      const url = URL.createObjectURL(file);
      document.body.style.backgroundImage = `url(${url})`;
    });

    // 音乐导入与播放
    const musicBtn = document.getElementById('musicBtn');
    const musicUpload = document.getElementById('musicUpload');
    const bgMusic = document.getElementById('bgMusic');

    musicBtn.addEventListener('click', () => {
      musicUpload.click();
    });
    musicUpload.addEventListener('change', e => {
      const file = e.target.files[0];
      const url = URL.createObjectURL(file);
      bgMusic.src = url;
      bgMusic.play();
    });

    // 图片导入
    document.getElementById('imgUpload1').addEventListener('change', e => {
      const file = e.target.files[0];
      const url = URL.createObjectURL(file);
      document.getElementById('img1').style.backgroundImage = `url(${url})`;
    });
    document.getElementById('imgUpload2').addEventListener('change', e => {
      const file = e.target.files[0];
      const url = URL.createObjectURL(file);
      document.getElementById('img2').style.backgroundImage = `url(${url})`;
    });

    // 搜索聊天记录（示例）
    document.getElementById('searchBtn').addEventListener('click', () => {
      const keyword = document.getElementById('searchInput').value;
      alert("搜索聊天记录: " + keyword + "（这里可接入IndexedDB查询）");
    });
  </script>
</body>
</html>
