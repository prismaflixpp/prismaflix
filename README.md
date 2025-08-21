<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Vídeo Fullscreen</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<style>
  html, body { margin:0; height:100%; background:black; overflow: hidden; }
  #videoPlayer { 
    width: 100%; 
    height: 100%; 
    object-fit: cover; 
  }
  #overlay {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: rgba(0,0,0,0.8); /* escurece tudo */
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 10;
    cursor: pointer;
  }
  #overlay i {
    font-size: 120px;
    color: white;
  }
</style>
</head>
<body>

<video id="videoPlayer" controls></video>

<div id="overlay"><i class="fas fa-play"></i></div>

<script>
const params = new URLSearchParams(window.location.search);
const videoLink = params.get('link');
const video = document.getElementById('videoPlayer');
const overlay = document.getElementById('overlay');

if(videoLink) video.src = videoLink;

overlay.addEventListener('click', () => {
  video.play();
  if(video.requestFullscreen) video.requestFullscreen();
  overlay.style.display = 'none'; // remove overlay
});
</script>

</body>
</html>
