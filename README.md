<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Vídeo Fullscreen</title>
<style>
  html, body { margin:0; height:100%; background:black; }
  #videoPlayer { 
    width: 100%; 
    height: 100%; 
    object-fit: cover; 
  }
  #startOverlay {
    position: fixed;
    top:0; left:0;
    width: 100%; height: 100%;
    background: black;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 48px;
    color: white;
    font-weight: bold;
    cursor: pointer;
    z-index: 10;
  }
</style>
</head>
<body>

<video id="videoPlayer" controls></video>

<div id="startOverlay">CLIQUE PARA COMEÇAR</div>

<script>
const params = new URLSearchParams(window.location.search);
const videoLink = params.get('link');
const video = document.getElementById('videoPlayer');
const overlay = document.getElementById('startOverlay');

if(videoLink) video.src = videoLink;

overlay.addEventListener('click', () => {
  overlay.style.display = 'none'; // remove overlay
  video.play();                   // inicia vídeo
  if(video.requestFullscreen) video.requestFullscreen(); // fullscreen
});
</script>

</body>
</html>
