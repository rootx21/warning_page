<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <!--Import Google Icon Font-->
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
    <!--Import materialize.css-->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0-beta/css/materialize.min.css">

    <!--Let browser know website is optimized for mobile-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  </head>

  <body class="red darken-3 white-text">
    <div class="container">
      
      <h1><img style="width: 20%; margin-right: 20px; vertical-align: middle;" src="icon.png" alt="">緊急地震速報</h1>
      <h4>岩手県沖で震度7の地震を確認しました。</br>津波や土砂崩れが発生する恐れがありま</br>すので直ちに避難してください。</h4>
　　<a href="https://www.amazon.co.jp/ミドリ安全-ヘルメット-クリアバイザー-通気孔付-　　　SC11PCLV/dp/B002SOPAOW/ref=sr_1_2_sspa?__mk_ja_JP=カタカナ&dchild=1&keywords=安全ヘルメット　　　　　　　　　　　　　&qid=1627875671&sr=8spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUFLMEJWWVlaVTY3UFEmZ
　　　W5jcnlwdGVkSWQ9QTAxMTE5OTYxWlNTU1UzQlVLVFRRJmVuY3J5cHRlZEFkSWQ9QTJORTdTUkU3WDZVSjMmd2　　　　　
　　　lkZ2V0TmFtZT1zcF9hdGYmYWN0aW9uPWNsaWNrUmVkaXJlY3QmZG9Ob3RMb2dDbGljaz10cnVl" class="btn btn-laege">了解</a>
    </div>
    <div id="alert" class="modal">
      <div class="modal-content black-text">
        <h4>緊急地震速報</h4>
        <p>岩手県沖で震度7の地震が発生しました。</br>直ちに避難してください。</p>
      </div>
      <div class="modal-footer">
        <button id="close" class="btn btn-laege">OK</button>d
      </div>
    </div>
    <!--JavaScript at end of body for optimized loading-->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0-beta/js/materialize.min.js"></script>
    <script>
      function play_se(){
        // SEとバイブレーションの制御
        var warning = new Audio('jishin.mp3.mp3');
        warning.play();
        navigator.vibrate([200, 100, 200, 100, 200, 100, 200]);
      }
      $(function(){
        // ブラウザバック禁止
        history.pushState(null, null, null);
        $(window).on("popstate", function(e){
          if (!e.originalEvent.state){
            play_se();
            history.pushState(null, null, null);
            return;
          }
        });

        // モーダル初期化
        $('.modal').modal({dismissible: false});
        $('#alert').modal('open');
        $('#close').click(function(){
          $('#alert').modal('close');
          play_se();
        });

        var device = navigator.userAgent.match(/Android|iPhone|iPad/);
        if (device == null){
          device = '端末';
        }
        $('#device').text(device);

        var time = 60;
        setInterval(function(){
          time--;
          $('#timer').text(time);
        }, 1000);
      });
    </script>
  </body>
</html>
