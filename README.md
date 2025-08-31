
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>My Video Website</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
      color: #fff;
    }
    header {
      background: #141e30;
      padding: 1.2rem;
      text-align: center;
      position: sticky;
      top: 0;
      z-index: 100;
    }
    header h1 {
      margin: 0;
      color: #ffd369;
      font-size: 2rem;
    }
    nav {
      margin-top: 0.5rem;
    }
    nav a {
      margin: 0 1rem;
      color: #ffd369;
      text-decoration: none;
      font-weight: bold;
      transition: 0.3s;
    }
    nav a:hover {
      color: #fff;
    }
    section {
      padding: 2rem;
      max-width: 1100px;
      margin: auto;
    }
    h2 {
      margin-bottom: 1rem;
      color: #ffd369;
      border-bottom: 2px solid #ffd369;
      padding-bottom: 5px;
    }
    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.5rem;
    }
    .video-card {
      background: #1b2a38;
      border-radius: 12px;
      padding: 1rem;
      box-shadow: 0 4px 8px rgba(0,0,0,0.4);
      transition: transform 0.3s;
    }
    .video-card:hover {
      transform: scale(1.02);
    }
    .video-card video {
      width: 100%;
      border-radius: 10px;
      margin-bottom: 0.5rem;
    }
    .caption {
      font-size: 0.9rem;
      color: #ddd;
      text-align: center;
    }
    .upload-box {
      background: #16222a;
      padding: 1rem;
      border-radius: 10px;
      margin-bottom: 2rem;
      text-align: center;
      border: 1px dashed #ffd369;
    }
    input[type="file"], input[type="text"] {
      margin: 0.5rem 0;
      padding: 0.4rem;
    }
    button {
      background: #ffd369;
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 6px;
      font-weight: bold;
      cursor: pointer;
      transition: 0.3s;
    }
    button:hover {
      background: #e6b347;
    }
  </style>
</head>
<body>
  <header>
    <h1>🎬 My Video Website</h1>
    <nav>
      <a href="#hollywood">Hollywood</a>
      <a href="#bollywood">Bollywood</a>
      <a href="#anime">Anime</a>
    </nav>
  </header>

  <!-- Hollywood Section -->
  <section id="hollywood">
    <h2>Hollywood Section</h2>
    <div class="upload-box admin-only">
      <input type="file" id="hollywoodUpload" accept="video/*" />
      <input type="text" id="hollywoodCaption" placeholder="Enter video caption..." />
      <button onclick="uploadVideo('hollywoodUpload','hollywoodGallery','hollywoodCaption')">Upload</button>
    </div>
    <div class="gallery" id="hollywoodGallery"></div>
  </section>

  <!-- Bollywood Section -->
  <section id="bollywood">
    <h2>Bollywood Section</h2>
    <div class="upload-box admin-only">
      <input type="file" id="bollywoodUpload" accept="video/*" />
      <input type="text" id="bollywoodCaption" placeholder="Enter video caption..." />
      <button onclick="uploadVideo('bollywoodUpload','bollywoodGallery','bollywoodCaption')">Upload</button>
    </div>
    <div class="gallery" id="bollywoodGallery"></div>
  </section>

  <!-- Anime Section -->
  <section id="anime">
    <h2>Anime Section</h2>
    <div class="upload-box admin-only">
      <input type="file" id="animeUpload" accept="video/*" />
      <input type="text" id="animeCaption" placeholder="Enter video caption..." />
      <button onclick="uploadVideo('animeUpload','animeGallery','animeCaption')">Upload</button>
    </div>
    <div class="gallery" id="animeGallery"></div>
  </section>

  <script>
    // ADMIN PASSWORD (only uploader can see upload boxes)
    const ADMIN_PASSWORD = "ayush123"; // 👉 এখানে আপনার পাসওয়ার্ড লিখুন
    const isAdmin = prompt("Enter admin password:") === ADMIN_PASSWORD;

    // Hide upload boxes if not admin
    if (!isAdmin) {
      document.querySelectorAll('.admin-only').forEach(el => el.style.display = 'none');
    }

    // Video upload function
    function uploadVideo(inputId, galleryId, captionId) {
      const input = document.getElementById(inputId);
      const captionText = document.getElementById(captionId).value;
      const gallery = document.getElementById(galleryId);

      if (input.files.length > 0) {
        const file = input.files[0];
        const url = URL.createObjectURL(file);

        const card = document.createElement('div');
        card.className = 'video-card';

        const video = document.createElement('video');
        video.src = url;
        video.controls = true;

        const caption = document.createElement('div');
        caption.className = 'caption';
        caption.textContent = captionText || "No description";

        card.appendChild(video);
        card.appendChild(caption);
        gallery.appendChild(card);
      }
    }
  </script>
</body>
</html>
