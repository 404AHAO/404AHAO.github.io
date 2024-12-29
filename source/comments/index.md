---
title: 留言板
top_img: false
type: envelope
# date: 2023-08-09 11:15:55
---


<!-- <div class="poem-wrap">
  <div class="poem-border poem-left"></div>
  <div class="poem-border poem-right"></div>
  <h1>热评</h1>  
  <p id="poem">loading...</p>
  <p id="info">loading...</p>
</div>

<script>
  function updateComment() {
    fetch("https://api.qjqq.cn/api/Yi?c=j")     //句子类型可以更换
      .then(response => {
        if (!response.ok) {
          throw new Error("Network response was not ok");
        }
        return response.json();
      })
      .then(data => {

        const poemElement = document.getElementById('poem');
        const infoElement = document.getElementById('info');
        poemElement.innerHTML = data.hitokoto;
        if (data.from_who !== null) {
          infoElement.innerHTML = data.from_who + " · " + "《 " + data.from + " 》";
        } else {
          infoElement.innerHTML = " “ " + data.from + " ” ";
        }
      })
      .catch(error => {

        const poemElement = document.getElementById('poem');
        const infoElement = document.getElementById('info');
        poemElement.innerHTML = "获取出错啦";
        infoElement.innerHTML = "";
        console.error('Fetch error:', error);
      });
  }

  updateComment();

  window.addEventListener('load', updateComment);
</script> -->


<!-- <script>
  infos = ['群主最帅', '石头最漂亮', '这是一条弹幕', '前端太难了', '好烦']

  setInterval(function() {
    for (r in infos) {
      //设置弹幕的样式和内容
      info = $('<span></span>');
      info.text(infos[r]);
      info.attr("style", "margin-right:0px;margin-top:" + Math.random() * 35 + "%;position:absolute;color:white;");
      //向弹幕显示区域添加弹幕
      $('#main').append(info);
      //设置动画
      info.animate({
        left: 0
      }, 8000, 'linear', function() {
      //动画完成后就删除
      $(this).remove();
      });
    }

}, 3000);
</script> -->
