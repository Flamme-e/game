<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Nowhere House</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Freckle+Face&display=swap');
    @import url('https://fonts.googleapis.com/css2?family=Jolly+Lodger&display=swap');
    
    /*STARTING INTERFACE*/
    /* Background video styling */
    video {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      z-index: -2;
    }
    
    /* Dark overlay to deepen the atmosphere */
    body::before {
      content: "";
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(19, 3, 3, 0.5);
      z-index: -1;
    }

    body {
      margin: 0;
      padding: 0;
      font-family: 'Freckle Face', cursive;
      background-size: cover;
      min-height: 100vh;
      color: rgba(124, 0, 0, 0.952);
      height: 100vh;
    }

    .menu-container {
      position: absolute;
      top: 75%;
      right: 6%;
      transform: translateY(-50%);
      text-align: right;
    }

    .menu {
      display: flex;
      flex-direction: column;
    }

    .menu a {
      display: block;
      margin: 10px 0;
      text-decoration: none;
      color: rgba(218, 218, 218, 0.87);
      font-size: 40px;
      transition: letter-spacing 0.3s ease, text-shadow 0.3s ease, color 0.3s ease;
      text-align: left;
      font-weight: bold;
      text-shadow: 5px 4px 5px #000000;
    }

    /* New Glow Animation */
    @keyframes glow {
      0% {
        transform: scale(1);
        text-shadow: 0 0 5px rgba(255,0,0,0.7), 0 0 10px rgba(255,0,0,0.5);
      }
      50% {
        transform: scale(1.1);
        text-shadow: 0 0 15px rgba(255,0,0,1), 0 0 20px rgba(255,0,0,0.8);
      }
      100% {
        transform: scale(1);
        text-shadow: 0 0 5px rgba(255,0,0,0.7), 0 0 10px rgba(255,0,0,0.5);
      }
    }

    .menu a:hover {
      color: red;
      animation: glow 1s ease-in-out infinite;
    }

    /* Style for the page containers (hidden by default) */
    .page-container {
      display: none;
      padding: 20px;
      color: #eee;
      font-size: 22px;
    }

    /*PLAY BUTTON*/
    /* Trigger Warning Modal Styles */
    .jumpscare {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      z-index: -2;
    }


    .modal {
      display: none; /* Hidden by default */
      position: fixed;
      z-index: 1000; /* On top of everything */
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      overflow: auto;
      background-color: rgba(0,0,0,0.8);
    }
    
    .modal-content {
      background-color: #9400008a;
      margin: 15% auto;
      padding: 30px;
      border: 3px solid #949494d5;
      width: 80%;
      max-width: 500px;
      text-align: center;
      color: #000000;
      font-family: 'Jolly Lodger', cursive;
      text-align: center;
    }
    
    .modal-content h2 {
      margin-top: 0;
      font-size: 40px;
      color: rgb(255, 187, 187);
    }
    
    .modal-content p {
      font-size: 25px; 
    }

    .modal-buttons {
      margin-top: 20px;
    }
    
    /* Modal Buttons with Color and Animation */
    .modal-buttons button {
      padding: 15px 20px;
      margin: 0 10px;
      font-size: 16px;
      cursor: pointer;
      border: none;
      border-radius: 5px;
      color: rgb(255, 187, 187);
      transition: transform 0.2s ease, background-color 0.3s ease;
    }

    #continue-btn {
      background-color: rgba(0,0,0,0.5); 
    }

    #cancel-btn {
      background-color: rgba(0,0,0,0.5); 
    }
    
    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.1); }
      100% { transform: scale(1); }
    }
    
    .modal-buttons button:hover {
      animation: pulse 1s infinite;
    }

   
  </style>
</head>
<body>
  <video loop autoplay muted src="final.mp4"></video>
  <!-- Homepage Container -->
  <div id="home-container">
    <div class="menu-container">
      <div class="menu">
        <a href="#" id="play-btn">PLAY</a>
        <a href="#" id="gallery-btn">GALLERY</a>
        <a href="#" id="about-btn">ABOUT</a>
        <a href="#" id="tutorials-btn">TUTORIALS</a>
        <a href="#" id="settings-btn">SETTINGS</a>
      </div>
    </div>
  </div>

  <!-- Trigger Warning Modal -->
  <div id="trigger-warning-modal" class="modal">
    <div class="modal-content">
      <h2>Trigger Warning</h2>
      <p>This visual novel contains themes and imagery that may be distressing for some players. The content includes references to graphic violence, death, and body dissolution through chemical means, as well as elements of psychological horror and supernatural phenomena. If you are sensitive to or triggered by depictions of violence, body horror, or traumatic events, please proceed with caution.</p>
      <div class="modal-buttons">
        <button id="continue-btn">Continue</button>
        <button id="cancel-btn">Cancel</button>
      </div>
    </div>
  </div>

  <!-- Page Containers -->
  <div id="play-container" class="page-container">
    <div class="jumpscare">
      <img src="https://images-ng.pixai.art/images/orig/58128b09-6034-4bc5-9540-7d11cd690c63" alt="Jumpscare" width="100%" height="100%">
    </div>
      <div class="dialogue-box">
        <p>
          You pull out an old yearbook and carefully flip through its worn pages, scanning for the name that has haunted you. 
          Suddenly, your eyes lock onto a page where a photograph has been torn out—so badly ripped that the girl's face is nearly 
          unrecognizable. Yet, beneath the smudged image, one name stands out: <strong>Lyris Sinclair</strong>. A shock of recognition jolts through you.
        </p>
      </div>
    
      <!-- Choice Buttons -->
      <div class="choice-container">
        <button class="choice" id="choice1">Examine the Torn Page Closely</button>
        <button class="choice" id="choice2">File It for Later</button>
      </div>
    </div>
  
  </div>
  <div id="gallery-container" class="page-container">
    <h2>Gallery Page</h2>
    <p>This is the gallery page content.</p>
  </div>
  <div id="about-container" class="page-container">
    <h2>About Page</h2>
    <p>This is the about page content.</p>
  </div>
  <div id="tutorials-container" class="page-container">
    <h2>Tutorials Page</h2>
    <p>This is the tutorials page content.</p>
  </div>
  <div id="settings-container" class="page-container">
    <h2>Settings Page</h2>
    <p>This is the settings page content.</p>
  </div>

  <script>
    // Function to hide the homepage and show the selected page
    function showPage(pageId) {
      // Hide the homepage container
      document.getElementById('home-container').style.display = 'none';

      // Hide all page containers first
      var pages = document.getElementsByClassName('page-container');
      for (var i = 0; i < pages.length; i++) {
        pages[i].style.display = 'none';
      }

      // Display the selected container
      document.getElementById(pageId).style.display = 'block';
    }

    // Event listener for the PLAY button to show the trigger warning modal
    document.getElementById('play-btn').addEventListener('click', function(e) {
      e.preventDefault();
      document.getElementById('trigger-warning-modal').style.display = 'block';
    });

    // Event listener for the Continue button in the modal
    document.getElementById('continue-btn').addEventListener('click', function(e) {
      e.preventDefault();
      document.getElementById('trigger-warning-modal').style.display = 'none';
      showPage('play-container');
    });

    // Event listener for the Cancel button in the modal
    document.getElementById('cancel-btn').addEventListener('click', function(e) {
      e.preventDefault();
      document.getElementById('trigger-warning-modal').style.display = 'none';
    });

    // Event listeners for other menu buttons
    document.getElementById('gallery-btn').addEventListener('click', function(e) {
      e.preventDefault();
      showPage('gallery-container');
    });

    document.getElementById('about-btn').addEventListener('click', function(e) {
      e.preventDefault();
      showPage('about-container');
    });

    document.getElementById('tutorials-btn').addEventListener('click', function(e) {
      e.preventDefault();
      showPage('tutorials-container');
    });

    document.getElementById('settings-btn').addEventListener('click', function(e) {
      e.preventDefault();
      showPage('settings-container');
    });
  </script>
</body>
</html>
