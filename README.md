<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Vídeo Fullscreen</title>
  <style>
    html, body {
      margin: 0;
      height: 100%;
      background: black;
    }
    iframe {
      width: 100%;
      height: 100%;
      border: none;
    }
  </style>
</head>
<body>
  <iframe id="videoFrame" allowfullscreen allowtransparency allow="autoplay" scrolling="no"></iframe>

  <script>
    // Pega o parâmetro 'link' da URL
    const params = new URLSearchParams(window.location.search);
    const videoLink = params.get('link');

    const iframe = document.getElementById('videoFrame');
    if(videoLink) {
      iframe.src = videoLink;
    } else {
      document.body.innerHTML = "Nenhum link de vídeo fornecido!";
    }
  </script>
</body>
</html>
