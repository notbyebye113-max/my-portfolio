<style>
  /* Masonry layout */
  .masonry {
    column-count: 1;
    column-gap: 1rem;
  }

  @media (min-width: 640px) {
    .masonry {
      column-count: 2;
    }
  }

  @media (min-width: 1024px) {
    .masonry {
      column-count: 3;
    }
  }

  .masonry-item {
    break-inside: avoid;
    margin-bottom: 1rem;
    overflow: hidden;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  }

  .masonry-item img {
    width: 100%;
    display: block;
    border-radius: 12px;
    transition: transform .4s ease;
  }

  .masonry-item img:hover {
    transform: scale(1.05);
  }
</style>

<div class="masonry reveal">
  
  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7400001.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1548545811-92523297a7da?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409308.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409325.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409977.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC06869.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1606800052052-a08af7148866?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC06887.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC07259.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1606800052052-a08af7148866?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC07277.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/IMG_8711.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/IMG_8723.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1623167198303-3453b3b64415?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/IMG_8813.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
  </div>

</div>
