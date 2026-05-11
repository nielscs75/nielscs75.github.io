<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Question pour Sofía :))</title>
  
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.9.3/dist/confetti.browser.min.js"></script>
  
  <style>
    :root {
      --bg1: #ffd6e7;
      --bg2: #ffeef6;
      --yes: #ff3b7a;
    }

    * { box-sizing: border-box; }

    body { 
      margin: 0; 
      min-height: 100vh; 
      display: flex; 
      justify-content: center; 
      align-items: center; 
      background: radial-gradient(circle at top, var(--bg2), var(--bg1)); 
      font-family: system-ui, -apple-system, sans-serif; 
      text-align: center; 
      /* Correction : Autorise le défilement si le contenu dépasse */
      overflow-y: auto; 
      overflow-x: hidden; 
      padding: 20px;
    }

    #confettiCanvas {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 9999;
    }

    .card { 
      background: rgba(255, 255, 255, 0.9); 
      padding: 30px 20px; 
      border-radius: 25px; 
      box-shadow: 0 15px 35px rgba(0,0,0,0.1); 
      width: 100%; 
      max-width: 450px; 
      position: relative;
      margin: auto; 
      backdrop-filter: blur(5px);
    }

    .art {
      width: 160px;
      height: auto;
      margin: 0 auto 15px;
      display: block;
      filter: drop-shadow(0 8px 12px rgba(0,0,0,0.1));
    }

    h1 { 
      font-size: clamp(20px, 5vw, 26px); 
      color: #333; 
      margin-bottom: 20px; 
      line-height: 1.3; 
      padding: 0 10px;
    }

    .buttons-container { 
      position: relative; 
      height: 140px; 
      width: 100%; 
      margin-top: 10px;
    }

    button { 
      font-size: 16px; 
      font-weight: 800; 
      padding: 14px 22px; 
      border: none; 
      border-radius: 50px; 
      cursor: pointer; 
      position: absolute; 
      transition: top 0.15s ease, left 0.15s ease, transform 0.2s; 
      user-select: none;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
      white-space: nowrap;
    }

    #yesBtn { 
      background: var(--yes); 
      color: white; 
      left: 10%; 
      top: 30%; 
      z-index: 10;
    }

    #noBtn { 
      background: #e5e7eb; 
      color: black; 
      right: 10%; 
      top: 30%; 
      z-index: 100; /* Toujours au dessus pour être capté par la souris */
    }

    #hint { font-size: 14px; color: #666; margin-top: 20px; font-style: italic; }
    
    #result { display: none; margin-top: 20px; animation: pop 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275); }
    
    .result-title {
      font-size: 28px;
      color: #333;
      margin-bottom: 15px;
      font-weight: 900;
    }

    .zebra-img { 
      width: 100%; 
      max-width: 300px;
      border-radius:
