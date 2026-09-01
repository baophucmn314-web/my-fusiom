```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Object Show Studio — Portfolio v2</title>

<style>
:root{
  --bg:#0c0d12;
  --surface:#151720;
  --surface2:#1d202b;
  --surface3:#272b38;
  --text:#f5f6fa;
  --muted:#9298aa;
  --line:#343948;
  --yellow:#ffd43b;
  --orange:#ff884d;
  --green:#62d68b;
  --red:#ff6262;
  --blue:#70a7ff;
  --shadow:0 20px 60px rgba(0,0,0,.35);
}

*{box-sizing:border-box;margin:0;padding:0}

html{scroll-behavior:smooth}

body{
  background:
    radial-gradient(circle at 10% 0%,rgba(255,212,59,.08),transparent 30%),
    radial-gradient(circle at 90% 20%,rgba(112,167,255,.06),transparent 30%),
    var(--bg);
  color:var(--text);
  font-family:Inter,Arial,sans-serif;
  line-height:1.5;
}

button,input,textarea,select{font:inherit}

button{cursor:pointer}

a{color:inherit;text-decoration:none}

/* NAV */

.nav{
  position:fixed;
  z-index:1000;
  top:0;
  left:0;
  right:0;
  height:70px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:0 5%;
  background:rgba(12,13,18,.86);
  backdrop-filter:blur(18px);
  border-bottom:1px solid var(--line);
}

.brand{
  display:flex;
  align-items:center;
  gap:12px;
  font-weight:900;
}

.brand-mark{
  width:40px;
  height:40px;
  display:grid;
  place-items:center;
  background:var(--yellow);
  color:#111;
  border:2px solid #111;
  border-radius:11px;
  box-shadow:4px 4px 0 #000;
  transform:rotate(-4deg);
}

.nav-links{
  display:flex;
  gap:20px;
}

.nav-links a{
  color:var(--muted);
  font-weight:700;
}

.nav-links a:hover{color:var(--yellow)}

.dashboard-btn{
  border:1px solid var(--line);
  background:var(--surface);
  color:var(--text);
  padding:9px 14px;
  border-radius:10px;
  font-weight:800;
}

.dashboard-btn:hover{
  border-color:var(--yellow);
}

/* HERO */

.hero{
  min-height:100vh;
  display:grid;
  place-items:center;
  text-align:center;
  padding:120px 6% 70px;
  position:relative;
  overflow:hidden;
}

.hero-inner{
  max-width:950px;
  position:relative;
  z-index:2;
}

.eyebrow{
  display:inline-block;
  padding:7px 14px;
  border:1px solid var(--line);
  border-radius:999px;
  background:var(--surface);
  color:var(--yellow);
  font-size:.8rem;
  font-weight:900;
  letter-spacing:.08em;
}

.hero h1{
  margin-top:22px;
  font-size:clamp(4rem,11vw,9rem);
  line-height:.83;
  letter-spacing:-.07em;
  text-shadow:8px 8px 0 #000;
  animation:bob 4s ease-in-out infinite;
}

.hero h1 span{color:var(--yellow)}

.hero p{
  max-width:650px;
  margin:30px auto;
  color:var(--muted);
  font-size:1.15rem;
}

.hero-buttons{
  display:flex;
  justify-content:center;
  gap:12px;
  flex-wrap:wrap;
}

.btn{
  border:1px solid var(--line);
  background:var(--surface);
  color:var(--text);
  padding:12px 18px;
  border-radius:12px;
  font-weight:900;
  transition:.2s;
}

.btn:hover{transform:translateY(-3px)}

.btn.primary{
  background:var(--yellow);
  color:#111;
  border-color:#111;
  box-shadow:5px 5px 0 #000;
}

/* OBJECT DECOR */

.floating-object{
  position:absolute;
  display:grid;
  place-items:center;
  user-select:none;
  pointer-events:none;
  filter:drop-shadow(5px 8px 0 #000);
}

.obj-star{
  width:90px;
  height:90px;
  background:var(--yellow);
  clip-path:polygon(
    50% 0%,61% 35%,98% 35%,
    68% 57%,79% 95%,50% 72%,
    21% 95%,32% 57%,2% 35%,39% 35%
  );
  animation:spinSlow 10s linear infinite;
}

.obj-ball{
  width:75px;
  height:75px;
  border-radius:50%;
  background:var(--orange);
  animation:float 3s ease-in-out infinite;
}

.obj-ball:after{
  content:"";
  width:17px;
  height:17px;
  border-radius:50%;
  background:#111;
  box-shadow:38px 3px 0 #111;
}

/* SECTIONS */

.section{
  width:min(1200px,92%);
  margin:auto;
  padding:100px 0;
}

.section-title{
  margin-bottom:35px;
}

.section-title h2{
  font-size:clamp(2.3rem,6vw,4.5rem);
  line-height:1;
}

.section-title p{
  color:var(--muted);
  margin-top:10px;
}

/* STATS */

.stats{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:15px;
}

.stat{
  background:var(--surface);
  border:1px solid var(--line);
  border-radius:18px;
  padding:24px;
}

.stat-number{
  display:block;
  font-size:2.5rem;
  font-weight:900;
  color:var(--yellow);
}

/* FILTERS */

.filters{
  display:flex;
  flex-wrap:wrap;
  gap:9px;
  margin-bottom:25px;
}

.filter{
  border:1px solid var(--line);
  background:var(--surface);
  color:var(--muted);
  padding:9px 15px;
  border-radius:999px;
  font-weight:800;
}

.filter.active,
.filter:hover{
  color:#111;
  background:var(--yellow);
}

/* PROJECTS */

.project-grid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(270px,1fr));
  gap:20px;
}

.project-card{
  background:var(--surface);
  border:1px solid var(--line);
  border-radius:20px;
  overflow:hidden;
  box-shadow:var(--shadow);
  animation:appear .5s ease both;
  transition:.25s;
}

.project-card:hover{
  transform:translateY(-7px);
  border-color:var(--yellow);
}

.project-cover{
  width:100%;
  aspect-ratio:16/10;
  object-fit:cover;
  display:block;
  background:var(--surface2);
}

.project-placeholder{
  aspect-ratio:16/10;
  display:grid;
  place-items:center;
  font-size:4rem;
  background:var(--surface2);
}

.project-info{padding:19px}

.project-info h3{font-size:1.3rem}

.project-info p{
  color:var(--muted);
  margin:7px 0 12px;
}

.tag{
  display:inline-block;
  padding:4px 8px;
  background:var(--surface3);
  color:var(--yellow);
  border-radius:7px;
  font-size:.7rem;
  font-weight:900;
}

/* VIDEOS */

.video-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(320px,1fr));
  gap:20px;
}

.video-card{
  background:var(--surface);
  border:1px solid var(--line);
  border-radius:20px;
  overflow:hidden;
}

.video-card iframe{
  width:100%;
  aspect-ratio:16/9;
  border:0;
  display:block;
}

.video-info{padding:18px}

.video-info p{
  color:var(--muted);
  margin-top:5px;
}

/* CHARACTERS */

.character-grid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(210px,1fr));
  gap:18px;
}

.character-card{
  background:var(--surface);
  border:1px solid var(--line);
  border-radius:22px;
  padding:22px;
  text-align:center;
  overflow:hidden;
  transition:.25s;
}

.character-card:hover{
  transform:translateY(-8px) rotate(-1deg);
  border-color:var(--yellow);
}

.character-art{
  width:130px;
  height:130px;
  margin:0 auto 18px;
  border-radius:30%;
  background:var(--surface2);
  display:grid;
  place-items:center;
  font-size:4rem;
  animation:characterBob 3s ease-in-out infinite;
  box-shadow:0 10px 25px rgba(0,0,0,.25);
}

.character-art img{
  width:100%;
  height:100%;
  object-fit:contain;
  border-radius:inherit;
}

.character-card h3{font-size:1.25rem}

.character-meta{
  color:var(--muted);
  font-size:.9rem;
  margin-top:4px;
}

.role{
  display:inline-block;
  margin-top:12px;
  padding:5px 10px;
  border-radius:999px;
  background:var(--yellow);
  color:#111;
  font-size:.7rem;
  font-weight:900;
}

/* DASHBOARD */

.dashboard{
  position:fixed;
  z-index:2000;
  inset:0;
  background:rgba(5,6,10,.75);
  backdrop-filter:blur(12px);
  display:none;
}

.dashboard.open{display:block}

.dashboard-panel{
  position:absolute;
  right:0;
  top:0;
  bottom:0;
  width:min(650px,100%);
  overflow:auto;
  background:var(--surface);
  border-left:1px solid var(--line);
  padding:25px;
  animation:slideIn .3s ease;
}

.dashboard-header{
  display:flex;
  justify-content:space-between;
  align-items:center;
  margin-bottom:25px;
}

.close{
  width:38px;
  height:38px;
  border-radius:10px;
  border:1px solid var(--line);
  background:var(--surface2);
  color:var(--text);
  font-size:1.2rem;
}

.admin-tabs{
  display:flex;
  gap:7px;
  overflow:auto;
  margin-bottom:25px;
}

.admin-tab{
  white-space:nowrap;
  padding:9px 13px;
  border:1px solid var(--line);
  border-radius:10px;
  background:var(--surface2);
  color:var(--muted);
  font-weight:800;
}

.admin-tab.active{
  background:var(--yellow);
  color:#111;
}

.admin-page{display:none}
.admin-page.active{display:block}

.field{margin-bottom:16px}

.field label{
  display:block;
  margin-bottom:6px;
  color:var(--muted);
  font-size:.85rem;
  font-weight:800;
}

.field input,
.field textarea,
.field select{
  width:100%;
  padding:12px;
  border:1px solid var(--line);
  border-radius:10px;
  outline:none;
  background:var(--bg);
  color:var(--text);
}

.field textarea{
  min-height:110px;
  resize:vertical;
}

.field input:focus,
.field textarea:focus,
.field select:focus{
  border-color:var(--yellow);
}

.form-row{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:12px;
}

.admin-list{
  display:grid;
  gap:10px;
}

.admin-item{
  display:flex;
  gap:12px;
  align-items:center;
  padding:12px;
  background:var(--surface2);
  border:1px solid var(--line);
  border-radius:12px;
}

.admin-thumb{
  width:55px;
  height:55px;
  object-fit:cover;
  border-radius:9px;
  background:var(--surface3);
}

.admin-item-main{
  flex:1;
  min-width:0;
}

.admin-item-main strong{
  display:block;
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
}

.admin-item-main small{color:var(--muted)}

.admin-actions{
  display:flex;
  gap:6px;
}

.icon-btn{
  width:35px;
  height:35px;
  border:1px solid var(--line);
  border-radius:8px;
  background:var(--bg);
  color:var(--text);
}

.icon-btn.delete:hover{
  background:var(--red);
}

.notice{
  padding:13px;
  border:1px solid var(--line);
  border-radius:11px;
  background:var(--surface2);
  color:var(--muted);
  margin-bottom:15px;
}

/* DROPZONE */

.dropzone{
  border:2px dashed var(--line);
  border-radius:18px;
  padding:35px 20px;
  text-align:center;
  transition:.2s;
}

.dropzone.dragover{
  border-color:var(--yellow);
  background:rgba(255,212,59,.06);
}

.dropzone input{display:none}

.dropzone strong{
  display:block;
  margin-bottom:5px;
}

/* GALLERY */

.gallery{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:10px;
  margin-top:15px;
}

.gallery-item{
  position:relative;
  aspect-ratio:1;
  border-radius:10px;
  overflow:hidden;
  border:1px solid var(--line);
}

.gallery-item img{
  width:100%;
  height:100%;
  object-fit:cover;
}

.gallery-remove{
  position:absolute;
  right:5px;
  top:5px;
  width:27px;
  height:27px;
  border:0;
  border-radius:50%;
  background:rgba(0,0,0,.75);
  color:#fff;
}

/* EMPTY */

.empty{
  text-align:center;
  padding:50px 20px;
  color:var(--muted);
  border:1px dashed var(--line);
  border-radius:18px;
}

/* FOOTER */

footer{
  border-top:1px solid var(--line);
  padding:45px 20px;
  text-align:center;
  color:var(--muted);
}

/* TOAST */

.toast{
  position:fixed;
  z-index:3000;
  right:20px;
  bottom:20px;
  max-width:350px;
  padding:13px 17px;
  background:var(--surface2);
  border:1px solid var(--line);
  border-radius:12px;
  box-shadow:var(--shadow);
  transform:translateY(120px);
  opacity:0;
  transition:.3s;
}

.toast.show{
  transform:translateY(0);
  opacity:1;
}

/* ANIMATIONS */

@keyframes bob{
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-9px)}
}

@keyframes float{
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-18px)}
}

@keyframes spinSlow{
  to{transform:rotate(360deg)}
}

@keyframes characterBob{
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-6px) rotate(1deg)}
}

@keyframes appear{
  from{opacity:0;transform:translateY(20px)}
  to{opacity:1;transform:translateY(0)}
}

@keyframes slideIn{
  from{transform:translateX(100%)}
  to{transform:translateX(0)}
}

/* RESPONSIVE */

@media(max-width:800px){
  .stats{grid-template-columns:1fr 1fr}
  .nav-links{display:none}
}

@media(max-width:550px){
  .stats{grid-template-columns:1fr}
  .form-row{grid-template-columns:1fr}
  .dashboard-panel{padding:18px}
}
</style>
</head>

<body>

<!-- =========================================================
     NAVIGATION
========================================================= -->

<nav class="nav">

  <a class="brand" href="#">
    <span class="brand-mark">★</span>
    <span>OBJECT SHOW STUDIO</span>
  </a>

  <div class="nav-links">
    <a href="#projects">Projects</a>
    <a href="#videos">Videos</a>
    <a href="#characters">Characters</a>
    <a href="#gallery">Gallery</a>
  </div>

  <button class="dashboard-btn" id="openDashboard">
    ⚙ Studio Dashboard
  </button>

</nav>


<!-- =========================================================
     HERO
========================================================= -->

<header class="hero">

  <div class="floating-object obj-star"
       style="left:8%;top:25%">
  </div>

  <div class="floating-object obj-ball"
       style="right:9%;top:35%">
  </div>

  <div class="hero-inner">

    <span class="eyebrow">
      ANIMATION • OBJECT SHOWS • WEB SERIES
    </span>

    <h1>
      MY <span>CREATIVE</span><br>
      WORLD
    </h1>

    <p>
      A professional portfolio for animation,
      object-show characters, contestants, hosts,
      web series and digital artwork.
    </p>

    <div class="hero-buttons">

      <a class="btn primary" href="#projects">
        Explore Portfolio →
      </a>

      <button class="btn" id="heroDashboard">
        Open Studio
      </button>

    </div>

  </div>

</header>


<!-- =========================================================
     STATS
========================================================= -->

<section class="section">

  <div class="stats">

    <div class="stat">
      <span class="stat-number" id="statProjects">0</span>
      Projects
    </div>

    <div class="stat">
      <span class="stat-number" id="statVideos">0</span>
      Videos
    </div>

    <div class="stat">
      <span class="stat-number" id="statCharacters">0</span>
      Characters
    </div>

    <div class="stat">
      <span class="stat-number" id="statImages">0</span>
      Gallery Images
    </div>

  </div>

</section>


<!-- =========================================================
     PROJECTS
========================================================= -->

<section class="section" id="projects">

  <div class="section-title">
    <h2>Projects</h2>
    <p>Organize your portfolio by production type.</p>
  </div>

  <div class="filters" id="projectFilters">

    <button class="filter active" data-filter="all">
      All
    </button>

    <button class="filter" data-filter="object-show">
      Object Show
    </button>

    <button class="filter" data-filter="animation">
      Animation
    </button>

    <button class="filter" data-filter="character">
      Character
    </button>

    <button class="filter" data-filter="web-series">
      Web Series
    </button>

  </div>

  <div class="project-grid" id="projectGrid"></div>

</section>


<!-- =========================================================
     VIDEOS
========================================================= -->

<section class="section" id="videos">

  <div class="section-title">
    <h2>YouTube</h2>
    <p>Your YouTube URLs automatically become embedded players.</p>
  </div>

  <div class="video-grid" id="videoGrid"></div>

</section>


<!-- =========================================================
     CHARACTERS
========================================================= -->

<section class="section" id="characters">

  <div class="section-title">
    <h2>Contestants & Hosts</h2>
    <p>
      Object-show character cards with role,
      gender and team information.
    </p>
  </div>

  <div class="character-grid" id="characterGrid"></div>

</section>


<!-- =========================================================
     GALLERY
========================================================= -->

<section class="section" id="gallery">

  <div class="section-title">
    <h2>Artwork Gallery</h2>
    <p>Upload artwork from your computer or drag files into the dashboard.</p>
  </div>

  <div class="gallery" id="publicGallery"></div>

</section>


<footer>
  © 2026 Object Show Studio — Animation Portfolio v2
</footer>


<!-- =========================================================
     DASHBOARD
========================================================= -->

<div class="dashboard" id="dashboard">

  <div class="dashboard-panel">

    <div class="dashboard-header">

      <div>
        <h2>Studio Dashboard</h2>
        <p style="color:var(--muted)">
          Manage your portfolio locally.
        </p>
      </div>

      <button class="close" id="closeDashboard">
        ×
      </button>

    </div>


    <div class="admin-tabs">

      <button class="admin-tab active"
              data-page="projectsAdmin">
        Projects
      </button>

      <button class="admin-tab"
              data-page="videosAdmin">
        YouTube
      </button>

      <button class="admin-tab"
              data-page="charactersAdmin">
        Characters
      </button>

      <button class="admin-tab"
              data-page="galleryAdmin">
        Gallery
      </button>

      <button class="admin-tab"
              data-page="backupAdmin">
        Backup
      </button>

    </div>


    <!-- PROJECT ADMIN -->

    <div class="admin-page active" id="projectsAdmin">

      <div class="notice">
        Create, edit and delete portfolio projects.
      </div>

      <div class="field">
        <label>Project title</label>
        <input id="projectTitle"
               placeholder="My Object Show">
      </div>

      <div class="field">
        <label>Description</label>
        <textarea id="projectDescription"
                  placeholder="Describe the project..."></textarea>
      </div>

      <div class="form-row">

        <div class="field">
          <label>Category</label>

          <select id="projectCategory">

            <option value="object-show">
              Object Show
            </option>

            <option value="animation">
              Animation
            </option>

            <option value="character">
              Character
            </option>

            <option value="web-series">
              Web Series
            </option>

          </select>
        </div>

        <div class="field">
          <label>Cover image URL</label>
          <input id="projectImage"
                 placeholder="https://...">
        </div>

      </div>

      <button class="btn primary"
              id="saveProject">
        + Add Project
      </button>

      <div class="admin-list"
           id="projectAdminList"
           style="margin-top:20px">
      </div>

    </div>


    <!-- VIDEO ADMIN -->

    <div class="admin-page" id="videosAdmin">

      <div class="notice">
        Paste almost any normal YouTube URL.
        The dashboard extracts the video ID automatically.
      </div>

      <div class="field">
        <label>YouTube URL</label>

        <input id="youtubeURL"
               placeholder="https://www.youtube.com/watch?v=...">
      </div>

      <div class="field">
        <label>Video title</label>

        <input id="youtubeTitle"
               placeholder="My Animation Episode">
      </div>

      <div class="field">
        <label>Description</label>

        <textarea id="youtubeDescription"
                  placeholder="About this video..."></textarea>
      </div>

      <button class="btn primary"
              id="addVideo">
        + Add YouTube Video
      </button>

      <div class="admin-list"
           id="videoAdminList"
           style="margin-top:20px">
      </div>

    </div>


    <!-- CHARACTER ADMIN -->

    <div class="admin-page" id="charactersAdmin">

      <div class="notice">
        Build contestant and host cards.
        Add gender, team and role metadata.
      </div>

      <div class="field">
        <label>Character name</label>

        <input id="characterName"
               placeholder="Example: Star">
      </div>

      <div class="form-row">

        <div class="field">
          <label>Gender</label>

          <select id="characterGender">

            <option>Male</option>
            <option>Female</option>
            <option>Non-binary</option>
            <option>Unknown</option>

          </select>
        </div>

        <div class="field">
          <label>Role</label>

          <select id="characterRole">

            <option>Contestant</option>
            <option>Host</option>
            <option>Co-host</option>
            <option>Guest</option>

          </select>
        </div>

      </div>

      <div class="form-row">

        <div class="field">
          <label>Team</label>

          <input id="characterTeam"
                 placeholder="Team 1">
        </div>

        <div class="field">
          <label>Object / emoji</label>

          <input id="characterEmoji"
                 value="⭐"
                 placeholder="⭐">
        </div>

      </div>

      <div class="field">
        <label>Character image URL</label>

        <input id="characterImage"
               placeholder="https://...">
      </div>

      <button class="btn primary"
              id="addCharacter">
        + Add Character
      </button>

      <div class="admin-list"
           id="characterAdminList"
           style="margin-top:20px">
      </div>

    </div>


    <!-- GALLERY ADMIN -->

    <div class="admin-page" id="galleryAdmin">

      <div class="notice">
        Drag multiple images directly into the drop zone.
        Images are stored locally in this browser.
      </div>

      <label class="dropzone"
             id="dropzone">

        <strong>
          Drop artwork here
        </strong>

        <span style="color:var(--muted)">
          or click to choose files
        </span>

        <input id="galleryUpload"
               type="file"
               accept="image/*"
               multiple>

      </label>

      <div class="gallery"
           id="adminGallery">
      </div>

    </div>


    <!-- BACKUP -->

    <div class="admin-page" id="backupAdmin">

      <div class="notice">
        Export your entire portfolio as JSON.
        Importing a backup replaces the current portfolio.
      </div>

      <button class="btn primary"
              id="exportJSON">
        ↓ Export Portfolio JSON
      </button>

      <br><br>

      <label class="btn"
             style="display:inline-block">

        ↑ Import Portfolio JSON

        <input id="importJSON"
               type="file"
               accept=".json"
               hidden>

      </label>

      <br><br>

      <button class="btn"
              id="clearPortfolio"
              style="color:var(--red)">
        Clear Entire Portfolio
      </button>

    </div>

  </div>

</div>


<!-- TOAST -->

<div class="toast" id="toast"></div>


<script>
/* =========================================================
   PORTFOLIO DATA
========================================================= */

const STORAGE_KEY = "objectShowPortfolioV2";

const defaultData = {

  projects: [

    {
      id: crypto.randomUUID(),
      title: "Korean Fried Chicken",
      description:
        "Object-show competition project featuring contestants and hosts.",
      category: "object-show",
      image: "",
    },

    {
      id: crypto.randomUUID(),
      title: "Fable Moon Star",
      description:
        "Fantasy object-show concept with character-driven competition.",
      category: "object-show",
      image: "",
    },

    {
      id: crypto.randomUUID(),
      title: "Weirdest to Unusual",
      description:
        "Experimental web-series concept.",
      category: "web-series",
      image: "",
    }

  ],

  videos: [],

  characters: [

    {
      id: crypto.randomUUID(),
      name: "Star",
      gender: "Unknown",
      role: "Contestant",
      team: "Team 1",
      emoji: "⭐",
      image: ""
    },

    {
      id: crypto.randomUUID(),
      name: "Moon",
      gender: "Unknown",
      role: "Host",
      team: "Host",
      emoji: "🌙",
      image: ""
    }

  ],

  gallery: []

};


let data =
  JSON.parse(localStorage.getItem(STORAGE_KEY))
  || defaultData;


/* =========================================================
   SAVE
========================================================= */

function save(){

  localStorage.setItem(
    STORAGE_KEY,
    JSON.stringify(data)
  );

  renderAll();
}


/* =========================================================
   TOAST
========================================================= */

let toastTimer;

function toast(message){

  const box =
    document.getElementById("toast");

  box.textContent = message;

  box.classList.add("show");

  clearTimeout(toastTimer);

  toastTimer =
    setTimeout(
      () => box.classList.remove("show"),
      2500
    );
}


/* =========================================================
   YOUTUBE URL CONVERTER
========================================================= */

function getYouTubeID(url){

  try{

    const parsed =
      new URL(url);

    if(
      parsed.hostname.includes("youtube.com")
    ){

      if(parsed.pathname === "/watch")
        return parsed.searchParams.get("v");

      if(parsed.pathname.startsWith("/shorts/"))
        return parsed.pathname.split("/")[2];

      if(parsed.pathname.startsWith("/embed/"))
        return parsed.pathname.split("/")[2];

    }

    if(
      parsed.hostname === "youtu.be"
    ){

      return parsed.pathname.slice(1);

    }

  }catch(error){

    return null;

  }

  return null;
}


/* =========================================================
   PROJECT RENDER
========================================================= */

let activeFilter = "all";

function renderProjects(){

  const grid =
    document.getElementById("projectGrid");

  grid.innerHTML = "";

  const list =
    data.projects.filter(project =>
      activeFilter === "all"
      || project.category === activeFilter
    );

  if(!list.length){

    grid.innerHTML =
      `<div class="empty">
        No projects in this category yet.
      </div>`;

    return;

  }

  list.forEach(project => {

    const card =
      document.createElement("article");

    card.className = "project-card";

    const image =
      project.image
      ? `<img class="project-cover"
              src="${escapeHTML(project.image)}"
              alt="${escapeHTML(project.title)}">`
      : `<div class="project-placeholder">
           🎬
         </div>`;

    card.innerHTML = `

      ${image}

      <div class="project-info">

        <span class="tag">
          ${escapeHTML(
            project.category.replace("-", " ").toUpperCase()
          )}
        </span>

        <h3>
          ${escapeHTML(project.title)}
        </h3>

        <p>
          ${escapeHTML(project.description)}
        </p>

      </div>

    `;

    grid.appendChild(card);

  });

}


/* =========================================================
   VIDEO RENDER
========================================================= */

function renderVideos(){

  const grid =
    document.getElementById("videoGrid");

  grid.innerHTML = "";

  if(!data.videos.length){

    grid.innerHTML =
      `<div class="empty">
        Add your first YouTube video from the dashboard.
      </div>`;

    return;

  }

  data.videos.forEach(video => {

    const card =
      document.createElement("article");

    card.className = "video-card";

    card.innerHTML = `

      <iframe
        src="https://www.youtube.com/embed/${encodeURIComponent(video.id)}"
        title="${escapeHTML(video.title)}"
        loading="lazy"
        allowfullscreen>
      </iframe>

      <div class="video-info">

        <h3>
          ${escapeHTML(video.title)}
        </h3>

        <p>
          ${escapeHTML(video.description)}
        </p>

      </div>

    `;

    grid.appendChild(card);

  });

}


/* =========================================================
   CHARACTER RENDER
========================================================= */

function renderCharacters(){

  const grid =
    document.getElementById("characterGrid");

  grid.innerHTML = "";

  if(!data.characters.length){

    grid.innerHTML =
      `<div class="empty">
        Add your first contestant or host.
      </div>`;

    return;

  }

  data.characters.forEach(character => {

    const card =
      document.createElement("article");

    card.className = "character-card";

    const art =
      character.image
      ? `<img src="${escapeHTML(character.image)}"
              alt="${escapeHTML(character.name)}">`
      : escapeHTML(character.emoji || "⭐");

    card.innerHTML = `

      <div class="character-art">
        ${art}
      </div>

      <h3>
        ${escapeHTML(character.name)}
      </h3>

      <div class="character-meta">
        ${escapeHTML(character.gender)}
        ·
        ${escapeHTML(character.team)}
      </div>

      <span class="role">
        ${escapeHTML(character.role)}
      </span>

    `;

    grid.appendChild(card);

  });

}


/* =========================================================
   GALLERY RENDER
========================================================= */

function renderGallery(){

  const publicGallery =
    document.getElementById("publicGallery");

  const adminGallery =
    document.getElementById("adminGallery");

  publicGallery.innerHTML = "";
  adminGallery.innerHTML = "";

  data.gallery.forEach((item,index) => {

    const publicItem =
      document.createElement("div");

    publicItem.className =
      "gallery-item";

    publicItem.innerHTML =
      `<img src="${item.image}"
            alt="${escapeHTML(item.name)}">`;

    publicGallery.appendChild(publicItem);


    const adminItem =
      document.createElement("div");

    adminItem.className =
      "gallery-item";

    adminItem.innerHTML = `

      <img src="${item.image}"
           alt="${escapeHTML(item.name)}">

      <button
        class="gallery-remove"
        data-gallery-index="${index}">
        ×
      </button>

    `;

    adminGallery.appendChild(adminItem);

  });

}


/* =========================================================
   ADMIN PROJECT LIST
========================================================= */

function renderProjectAdmin(){

  const list =
    document.getElementById("projectAdminList");

  list.innerHTML = "";

  data.projects.forEach(project => {

    const item =
      document.createElement("div");

    item.className = "admin-item";

    item.innerHTML = `

      ${
        project.image
        ? `<img class="admin-thumb"
                 src="${escapeHTML(project.image)}">`
        : `<div class="admin-thumb"></div>`
      }

      <div class="admin-item-main">

        <strong>
          ${escapeHTML(project.title)}
        </strong>

        <small>
          ${escapeHTML(project.category)}
        </small>

      </div>

      <div class="admin-actions">

        <button
          class="icon-btn"
          data-edit-project="${project.id}">
          ✎
        </button>

        <button
          class="icon-btn delete"
          data-delete-project="${project.id}">
          ×
        </button>

      </div>

    `;

    list.appendChild(item);

  });

}


/* =========================================================
   ADMIN VIDEO LIST
========================================================= */

function renderVideoAdmin(){

  const list =
    document.getElementById("videoAdminList");

  list.innerHTML = "";

  data.videos.forEach(video => {

    const item =
      document.createElement("div");

    item.className = "admin-item";

    item.innerHTML = `

      <div class="admin-thumb"
           style="display:grid;place-items:center">
        ▶
      </div>

      <div class="admin-item-main">

        <strong>
          ${escapeHTML(video.title)}
        </strong>

        <small>
          YouTube: ${escapeHTML(video.id)}
        </small>

      </div>

      <div class="admin-actions">

        <button
          class="icon-btn delete"
          data-delete-video="${video.id}">
          ×
        </button>

      </div>

    `;

    list.appendChild(item);

  });

}


/* =========================================================
   ADMIN CHARACTER LIST
========================================================= */

function renderCharacterAdmin(){

  const list =
    document.getElementById("characterAdminList");

  list.innerHTML = "";

  data.characters.forEach(character => {

    const item =
      document.createElement("div");

    item.className = "admin-item";

    item.innerHTML = `

      <div class="admin-thumb"
           style="display:grid;place-items:center;font-size:1.7rem">
        ${escapeHTML(character.emoji || "⭐")}
      </div>

      <div class="admin-item-main">

        <strong>
          ${escapeHTML(character.name)}
        </strong>

        <small>
          ${escapeHTML(character.role)}
          ·
          ${escapeHTML(character.gender)}
        </small>

      </div>

      <div class="admin-actions">

        <button
          class="icon-btn delete"
          data-delete-character="${character.id}">
          ×
        </button>

      </div>

    `;

    list.appendChild(item);

  });

}


/* =========================================================
   STATS
========================================================= */

function renderStats(){

  document.getElementById("statProjects")
    .textContent = data.projects.length;

  document.getElementById("statVideos")
    .textContent = data.videos.length;

  document.getElementById("statCharacters")
    .textContent = data.characters.length;

  document.getElementById("statImages")
    .textContent = data.gallery.length;

}


/* =========================================================
   ALL RENDER
========================================================= */

function renderAll(){

  renderProjects();
  renderVideos();
  renderCharacters();
  renderGallery();

  renderProjectAdmin();
  renderVideoAdmin();
  renderCharacterAdmin();

  renderStats();

}


/* =========================================================
   FILTERS
========================================================= */

document
  .getElementById("projectFilters")
  .addEventListener("click",event => {

    const button =
      event.target.closest(".filter");

    if(!button) return;

    document
      .querySelectorAll(".filter")
      .forEach(b =>
        b.classList.remove("active")
      );

    button.classList.add("active");

    activeFilter =
      button.dataset.filter;

    renderProjects();

  });


/* =========================================================
   ADD PROJECT
========================================================= */

document
  .getElementById("saveProject")
  .addEventListener("click",() => {

    const title =
      document.getElementById("projectTitle")
      .value.trim();

    const description =
      document.getElementById("projectDescription")
      .value.trim();

    const category =
      document.getElementById("projectCategory")
      .value;

    const image =
      document.getElementById("projectImage")
      .value.trim();

    if(!title){

      toast("Enter a project title.");

      return;

    }

    data.projects.unshift({

      id:crypto.randomUUID(),

      title,

      description:
        description || "Portfolio project.",

      category,

      image

    });

    document.getElementById("projectTitle").value="";
    document.getElementById("projectDescription").value="";
    document.getElementById("projectImage").value="";

    save();

    toast("Project added.");

  });


/* =========================================================
   EDIT PROJECT
========================================================= */

document.addEventListener("click",event => {

  const id =
    event.target.dataset.editProject;

  if(!id) return;

  const project =
    data.projects.find(p => p.id === id);

  if(!project) return;

  document.getElementById("projectTitle")
    .value = project.title;

  document.getElementById("projectDescription")
    .value = project.description;

  document.getElementById("projectCategory")
    .value = project.category;

  document.getElementById("projectImage")
    .value = project.image;

  data.projects =
    data.projects.filter(p => p.id !== id);

  save();

  toast("Project loaded into editor. Save it to create the updated version.");

});


/* =========================================================
   DELETE PROJECT
========================================================= */

document.addEventListener("click",event => {

  const id =
    event.target.dataset.deleteProject;

  if(!id) return;

  data.projects =
    data.projects.filter(
      project => project.id !== id
    );

  save();

  toast("Project deleted.");

});


/* =========================================================
   ADD VIDEO
========================================================= */

document
  .getElementById("addVideo")
  .addEventListener("click",() => {

    const url =
      document.getElementById("youtubeURL")
      .value.trim();

    const title =
      document.getElementById("youtubeTitle")
      .value.trim();

    const description =
      document.getElementById("youtubeDescription")
      .value.trim();

    const id =
      getYouTubeID(url);

    if(!id){

      toast("That doesn't look like a valid YouTube URL.");

      return;

    }

    data.videos.unshift({

      id,

      title:
        title || "YouTube Video",

      description:
        description || "Featured animation video."

    });

    document.getElementById("youtubeURL").value="";
    document.getElementById("youtubeTitle").value="";
    document.getElementById("youtubeDescription").value="";

    save();

    toast("YouTube video added.");

  });


/* =========================================================
   DELETE VIDEO
========================================================= */

document.addEventListener("click",event => {

  const id =
    event.target.dataset.deleteVideo;

  if(!id) return;

  data.videos =
    data.videos.filter(
      video => video.id !== id
    );

  save();

  toast("Video removed.");

});


/* =========================================================
   ADD CHARACTER
========================================================= */

document
  .getElementById("addCharacter")
  .addEventListener("click",() => {

    const name =
      document.getElementById("characterName")
      .value.trim();

    if(!name){

      toast("Enter a character name.");

      return;

    }

    data.characters.push({

      id:crypto.randomUUID(),

      name,

      gender:
        document.getElementById("characterGender").value,

      role:
        document.getElementById("characterRole").value,

      team:
        document.getElementById("characterTeam")
        .value.trim() || "Unassigned",

      emoji:
        document.getElementById("characterEmoji")
        .value.trim() || "⭐",

      image:
        document.getElementById("characterImage")
        .value.trim()

    });

    document.getElementById("characterName").value="";
    document.getElementById("characterTeam").value="";
    document.getElementById("characterImage").value="";

    save();

    toast("Character added.");

  });


/* =========================================================
   DELETE CHARACTER
========================================================= */

document.addEventListener("click",event => {

  const id =
    event.target.dataset.deleteCharacter;

  if(!id) return;

  data.characters =
    data.characters.filter(
      character => character.id !== id
    );

  save();

  toast("Character removed.");

});


/* =========================================================
   IMAGE UPLOAD
========================================================= */

function processImages(files){

  Array.from(files)
    .filter(file =>
      file.type.startsWith("image/")
    )
    .forEach(file => {

      const reader =
        new FileReader();

      reader.onload = event => {

        data.gallery.push({

          id:crypto.randomUUID(),

          name:file.name,

          image:event.target.result

        });

        save();

      };

      reader.readAsDataURL(file);

    });

}


/* =========================================================
   FILE INPUT
========================================================= */

document
  .getElementById("galleryUpload")
  .addEventListener("change",event => {

    processImages(event.target.files);

    event.target.value = "";

    toast("Artwork uploaded.");

  });


/* =========================================================
   DRAG & DROP
========================================================= */

const dropzone =
  document.getElementById("dropzone");

["dragenter","dragover"]
.forEach(eventName => {

  dropzone.addEventListener(
    eventName,
    event => {

      event.preventDefault();

      dropzone.classList.add("dragover");

    }
  );

});


["dragleave","drop"]
.forEach(eventName => {

  dropzone.addEventListener(
    eventName,
    event => {

      event.preventDefault();

      dropzone.classList.remove("dragover");

    }
  );

});


dropzone.addEventListener("drop",event => {

  processImages(event.dataTransfer.files);

  toast("Dropped artwork added.");

});


/* =========================================================
   DELETE GALLERY IMAGE
========================================================= */

document.addEventListener("click",event => {

  const index =
    event.target.dataset.galleryIndex;

  if(index === undefined) return;

  data.gallery.splice(
    Number(index),
    1
  );

  save();

  toast("Artwork removed.");

});


/* =========================================================
   DASHBOARD OPEN / CLOSE
========================================================= */

const dashboard =
  document.getElementById("dashboard");

function openDashboard(){

  dashboard.classList.add("open");

}

function closeDashboard(){

  dashboard.classList.remove("open");

}

document
  .getElementById("openDashboard")
  .addEventListener("click",openDashboard);

document
  .getElementById("heroDashboard")
  .addEventListener("click",openDashboard);

document
  .getElementById("closeDashboard")
  .addEventListener("click",closeDashboard);

dashboard.addEventListener("click",event => {

  if(event.target === dashboard)
    closeDashboard();

});


/* =========================================================
   ADMIN TABS
========================================================= */

document
  .querySelectorAll(".admin-tab")
  .forEach(tab => {

    tab.addEventListener("click",() => {

      document
        .querySelectorAll(".admin-tab")
        .forEach(t =>
          t.classList.remove("active")
        );

      document
        .querySelectorAll(".admin-page")
        .forEach(page =>
          page.classList.remove("active")
        );

      tab.classList.add("active");

      document
        .getElementById(tab.dataset.page)
        .classList.add("active");

    });

  });


/* =========================================================
   EXPORT JSON
========================================================= */

document
  .getElementById("exportJSON")
  .addEventListener("click",() => {

    const json =
      JSON.stringify(data,null,2);

    const blob =
      new Blob(
        [json],
        {type:"application/json"}
      );

    const url =
      URL.createObjectURL(blob);

    const a =
      document.createElement("a");

    a.href = url;

    a.download =
      "object-show-portfolio-backup.json";

    a.click();

    URL.revokeObjectURL(url);

    toast("Portfolio exported.");

  });


/* =========================================================
   IMPORT JSON
========================================================= */

document
  .getElementById("importJSON")
  .addEventListener("change",event => {

    const file =
      event.target.files[0];

    if(!file) return;

    const reader =
      new FileReader();

    reader.onload = () => {

      try{

        const imported =
          JSON.parse(reader.result);

        if(
          !imported.projects ||
          !imported.videos ||
          !imported.characters ||
          !imported.gallery
        ){

          throw new Error("Invalid portfolio");

        }

        data = imported;

        save();

        toast("Portfolio imported.");

      }catch(error){

        toast("Invalid portfolio JSON.");

      }

    };

    reader.readAsText(file);

    event.target.value = "";

  });


/* =========================================================
   CLEAR EVERYTHING
========================================================= */

document
  .getElementById("clearPortfolio")
  .addEventListener("click",() => {

    const confirmed =
      confirm(
        "Delete your entire portfolio? Export a backup first if needed."
      );

    if(!confirmed) return;

    data = {
      projects:[],
      videos:[],
      characters:[],
      gallery:[]
    };

    save();

    toast("Portfolio cleared.");

  });


/* =========================================================
   ESCAPE HTML
========================================================= */

function escapeHTML(value){

  const div =
    document.createElement("div");

  div.textContent =
    String(value ?? "");

  return div.innerHTML;

}


/* =========================================================
   INITIALIZE
========================================================= */

renderAll();

</script>

</body>
</html>
```
