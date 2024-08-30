<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The web site of heccster-manor</title>
    <link href="/style.css" rel="stylesheet" type="text/css" media="all">
  </head>
<body style="background-color:#000000; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100vh; margin: 0;">

<style>
body {
      font-family: "vcr"; 
      color: #FFFFFF; 
      text-decoration: none;
   }
 </style>
<div style="text-align:center;" class="icon-row">
  <a id="randomLink" onclick="openRandomVideo()">
    <img src="PlayButtonUtOBEN0001.png" id="videoIcon" style="position: centre;">
  </a>
  <video id="videoPlayer" style="display:none; position: centre;" controls=console loop="false"></video>
</div>
<script type="text/javascript">
  // Set the data-urls attribute using JavaScript.
  document.getElementById('randomLink').setAttribute('data-urls', 'https://heccster-manor.neocities.org/SHITE.txt');
</script>

<script>
  function openRandomVideo() {
    const randomLink = document.getElementById('randomLink');
    const urlsFile = randomLink.getAttribute('data-urls');
    
    fetch(urlsFile)
      .then(response => response.text())
      .then(data => {
        const urlList = data.split('\n');
        const randomIndex = Math.floor(Math.random() * urlList.length);
        const randomURL = urlList[randomIndex].trim();

        // Hide the image and display the video player
        document.getElementById('videoIcon').style.display = 'none';
        const videoPlayer = document.getElementById('videoPlayer');
        videoPlayer.style.display = 'block';
        videoPlayer.src = randomURL;
        videoPlayer.play();
        videoPlayer.loop = false;
      })
      .catch(error => {
        console.error('Error fetching and playing random video:', error);
      });
  }
</script>

<style>
  #randomLink {
    cursor: pointer; /* Set the cursor to pointer when hovering over the image */
  }
</style>

</body>

</html>
