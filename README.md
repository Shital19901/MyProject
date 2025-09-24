<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Travel Explorer — Creative Homepage</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    /* Smooth fades and subtle polish */
    .fade-in { animation: fadeIn .4s ease both; }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(6px) } to { opacity: 1; transform: translateY(0) } }

    /* Floating blobs background */
    .blob {
      position: absolute; border-radius: 9999px; filter: blur(48px); opacity: .25;
      animation: float 14s ease-in-out infinite;
    }
    @keyframes float {
      0%,100% { transform: translateY(0) }
      50% { transform: translateY(-20px) }
    }

    /* Animated globe */
    .spin-slow { animation: spin 28s linear infinite; }
    .pulse-soft { animation: pulseSoft 3s ease-in-out infinite; }
    @keyframes pulseSoft { 0%,100% { opacity:.7 } 50% { opacity:1 } }

    /* Lightbox entry */
    .lightbox-enter { animation: lb .2s ease both; }
    @keyframes lb { from { transform: scale(.96); opacity:0 } to { transform: scale(1); opacity:1 } }

    /* Hide scrollbars on carousels (visual clean-up) */
    .no-scrollbar::-webkit-scrollbar{display:none}
    .no-scrollbar{-ms-overflow-style:none;scrollbar-width:none}
  </style>
</head>
<body class="min-h-screen bg-gradient-to-br from-slate-950 via-indigo-950 to-blue-900 text-white selection:bg-white/20 selection:text-white font-[Inter,ui-sans-serif,system-ui]">
  <!-- Decorative blobs -->
  <div class="blob w-72 h-72 bg-fuchsia-500/40 -top-20 -left-10"></div>
  <div class="blob w-96 h-96 bg-cyan-500/40 top-32 -right-10" style="animation-delay:.7s"></div>
  <div class="blob w-80 h-80 bg-emerald-400/40 -bottom-20 left-24" style="animation-delay:1.4s"></div>

  <!-- Page Wrapper -->
  <div class="relative z-10 max-w-7xl mx-auto px-4 md:px-8">
    <!-- Nav -->
    <nav class="flex items-center justify-between py-5">
      <div class="flex items-center gap-3">
        <div class="w-10 h-10 rounded-xl bg-white/10 grid place-items-center ring-1 ring-white/15 shadow-lg">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="none" aria-hidden="true">
            <circle cx="12" cy="12" r="10" stroke="white" stroke-opacity=".9" stroke-width="1.5"/>
            <path d="M2 12h20M12 2c4 5 4 13 0 20M12 2c-4 5-4 13 0 20" stroke="white" stroke-opacity=".8" stroke-width="1.3"/>
          </svg>
        </div>
        <div class="leading-tight">
          <div class="text-lg font-semibold">Travel Explorer</div>
          <div class="text-xs text-white/60">Plan smarter. Explore beautifully.</div>
        </div>
      </div>
      <div class="hidden md:flex items-center gap-1">
        <a href="#features" class="px-3 py-2 rounded-lg hover:bg-white/10">Features</a>
        <a href="#destinations" class="px-3 py-2 rounded-lg hover:bg-white/10">Destinations</a>
        <a href="#how" class="px-3 py-2 rounded-lg hover:bg-white/10">How it works</a>
        <a href="#explore" class="px-3 py-2 rounded-lg bg-indigo-500 hover:bg-indigo-500/90 text-white ring-1 ring-white/10">Launch Explorer</a>
      </div>
      <button id="openExplorerTop" class="md:hidden px-3 py-2 rounded-lg bg-indigo-500 hover:bg-indigo-500/90 text-white">Explore</button>
    </nav>

    <!-- Hero -->
    <section class="mt-4 md:mt-10 grid grid-cols-1 lg:grid-cols-2 gap-8 items-center">
      <div class="order-2 lg:order-1">
        <h1 class="text-3xl md:text-5xl font-semibold leading-tight">
          Your next trip, beautifully planned.
        </h1>
        <p class="text-white/70 mt-3 md:mt-4 text-base md:text-lg">
          Browse stunning photos, peek at the weather, and save places you love. No setup needed — just search and go.
        </p>
        <div class="mt-6 flex flex-wrap gap-3">
          <a href="#explore" class="px-5 py-3 rounded-xl bg-indigo-500 hover:bg-indigo-500/90 text-white font-medium shadow-lg shadow-indigo-900/30">Launch Explorer</a>
          <a href="#destinations" class="px-5 py-3 rounded-xl bg-white/10 hover:bg-white/15 ring-1 ring-white/15">See popular places</a>
        </div>

        <!-- Mini weather peek -->
        <div class="mt-6 p-4 rounded-2xl bg-white/5 ring-1 ring-white/10">
          <form id="peekForm" class="grid grid-cols-1 sm:grid-cols-[1fr_auto] gap-3 items-stretch">
            <input id="peekCity" type="text" placeholder="Quick weather peek: Try Tokyo or Lisbon…" class="px-4 py-3 rounded-xl bg-white/10 ring-1 ring-white/15 outline-none placeholder:text-white/50 focus:ring-white/30">
            <button class="px-5 py-3 rounded-xl bg-emerald-500 hover:bg-emerald-500/90 text-white">Check</button>
          </form>
          <div id="peekResult" class="mt-3 text-sm text-white/80"></div>
        </div>
      </div>

      <!-- Animated Globe -->
      <div class="order-1 lg:order-2 relative aspect-square">
        <div class="absolute inset-0 rounded-full bg-gradient-to-br from-white/10 to-white/5 ring-1 ring-white/10"></div>
        <svg class="absolute inset-8 spin-slow" viewBox="0 0 400 400" fill="none" aria-hidden="true">
          <defs>
            <linearGradient id="lg" x1="0" x2="1" y1="0" y2="1">
              <stop offset="0%" stop-color="#93c5fd"/>
              <stop offset="100%" stop-color="#a78bfa"/>
            </linearGradient>
          </defs>
          <circle cx="200" cy="200" r="160" stroke="url(#lg)" stroke-opacity=".6" stroke-width="1.5"/>
          <ellipse cx="200" cy="200" rx="160" ry="60" stroke="url(#lg)" stroke-opacity=".4" stroke-width="1"/>
          <ellipse cx="200" cy="200" rx="160" ry="100" transform="rotate(90 200 200)" stroke="url(#lg)" stroke-opacity=".4" stroke-width="1"/>
          <ellipse cx="200" cy="200" rx="160" ry="130" transform="rotate(45 200 200)" stroke="url(#lg)" stroke-opacity=".25" stroke-width="1"/>
        </svg>
        <!-- Orbiting pins -->
        <div class="absolute left-1/2 top-10 -translate-x-1/2 w-2.5 h-2.5 rounded-full bg-rose-400 shadow-lg shadow-rose-900/50 pulse-soft"></div>
        <div class="absolute right-14 top-1/3 w-2.5 h-2.5 rounded-full bg-cyan-400 shadow-lg shadow-cyan-900/50 pulse-soft" style="animation-delay:.6s"></div>
        <div class="absolute left-10 bottom-14 w-2.5 h-2.5 rounded-full bg-amber-400 shadow-lg shadow-amber-900/50 pulse-soft" style="animation-delay:1.2s"></div>
        <!-- Caption card -->
        <div class="absolute -bottom-2 left-1/2 -translate-x-1/2 w-[92%] md:w-4/5 p-4 rounded-2xl bg-white/10 ring-1 ring-white/15 backdrop-blur-sm">
          <div class="text-sm text-white/80">Instant inspiration from around the world</div>
          <div class="text-xs text-white/60">Real photos • Quick weather • Save favorites</div>
        </div>
      </div>
    </section>

    <!-- Features -->
    <section id="features" class="mt-14 md:mt-20">
      <h2 class="text-2xl md:text-3xl font-semibold">Why you’ll love it</h2>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4 md:gap-6 mt-6">
        <div class="rounded-2xl p-5 bg-white/5 ring-1 ring-white/10">
          <div class="text-2xl mb-2">🖼️</div>
          <div class="font-semibold">Real photos, instantly</div>
          <p class="text-white/70 mt-1 text-sm">See authentic images powered by Wikipedia/Commons. Add an Unsplash key later for curated shots.</p>
        </div>
        <div class="rounded-2xl p-5 bg-white/5 ring-1 ring-white/10">
          <div class="text-2xl mb-2">🌤️</div>
          <div class="font-semibold">Weather at a glance</div>
          <p class="text-white/70 mt-1 text-sm">Get a quick temperature and wind snapshot using open data. No account required.</p>
        </div>
        <div class="rounded-2xl p-5 bg-white/5 ring-1 ring-white/10">
          <div class="text-2xl mb-2">⭐</div>
          <div class="font-semibold">Save and return</div>
          <p class="text-white/70 mt-1 text-sm">Bookmark favorite places so you can jump back in seconds.</p>
        </div>
      </div>
    </section>

    <!-- Popular Destinations -->
    <section id="destinations" class="mt-14 md:mt-20">
      <div class="flex items-center justify-between">
        <h2 class="text-2xl md:text-3xl font-semibold">Popular destinations</h2>
        <div class="text-sm text-white/70">Tap a chip to load a live photo grid</div>
      </div>
      <div class="mt-4 flex flex-wrap gap-2">
        <button class="chip px-3 py-1.5 rounded-full bg-white/10 hover:bg-white/15 ring-1 ring-white/15" data-place="Japan">Japan</button>
        <button class="chip px-3 py-1.5 rounded-full bg-white/10 hover:bg-white/15 ring-1 ring-white/15" data-place="Iceland">Iceland</button>
        <button class="chip px-3 py-1.5 rounded-full bg-white/10 hover:bg-white/15 ring-1 ring-white/15" data-place="Portugal">Portugal</button>
        <button class="chip px-3 py-1.5 rounded-full bg-white/10 hover:bg-white/15 ring-1 ring-white/15" data-place="Morocco">Morocco</button>
        <button class="chip px-3 py-1.5 rounded-full bg-white/10 hover:bg-white/15 ring-1 ring-white/15" data-place="New Zealand">New Zealand</button>
        <button class="chip px-3 py-1.5 rounded-full bg-white/10 hover:bg-white/15 ring-1 ring-white/15" data-place="Canada">Canada</button>
      </div>

      <div class="mt-5 rounded-2xl p-5 bg-white/5 ring-1 ring-white/10">
        <div class="flex items-center justify-between mb-3">
          <div class="font-semibold" id="popularTitle">Tap a destination to preview</div>
          <button id="openExplorerMid" class="text-sm px-3 py-1.5 rounded-lg bg-indigo-500 hover:bg-indigo-500/90">Open Explorer</button>
        </div>
        <div id="popularStatus" class="text-xs text-white/60 mb-3">Real images from Wikipedia/Commons.</div>
        <div id="popularGrid" class="grid grid-cols-2 md:grid-cols-3 gap-3 md:gap-4">
          <!-- filled dynamically -->
        </div>
      </div>
    </section>

    <!-- How it Works -->
    <section id="how" class="mt-14 md:mt-20">
      <h2 class="text-2xl md:text-3xl font-semibold">How it works</h2>
      <div class="mt-6 grid grid-cols-1 md:grid-cols-3 gap-4 md:gap-6">
        <div class="rounded-2xl p-5 bg-white/5 ring-1 ring-white/10">
          <div class="text-2xl">🔎</div>
          <div class="font-semibold mt-2">Search any place</div>
          <p class="text-white/70 text-sm mt-1">Type a city or country to see photos and a quick weather peek.</p>
        </div>
        <div class="rounded-2xl p-5 bg-white/5 ring-1 ring-white/10">
          <div class="text-2xl">🖱️</div>
          <div class="font-semibold mt-2">Open photos</div>
          <p class="text-white/70 text-sm mt-1">Tap a tile to view it large in a clean lightbox.</p>
        </div>
        <div class="rounded-2xl p-5 bg-white/5 ring-1 ring-white/10">
          <div class="text-2xl">📌</div>
          <div class="font-semibold mt-2">Save favorites</div>
          <p class="text-white/70 text-sm mt-1">Bookmark destinations for easy access later.</p>
        </div>
      </div>
    </section>

    <!-- Explorer CTA -->
    <section id="explore" class="mt-16 md:mt-24 mb-16">
      <div class="rounded-3xl overflow-hidden ring-1 ring-white/10 bg-gradient-to-br from-indigo-600/20 to-cyan-500/10">
        <div class="p-6 md:p-10">
          <div class="flex items-center justify-between flex-wrap gap-4">
            <div>
              <h3 class="text-xl md:text-2xl font-semibold">Jump in — Live Explorer</h3>
              <p class="text-white/70 text-sm md:text-base mt-1">Search places, see real photos, and a quick weather peek.</p>
            </div>
            <button id="openExplorerBtn" class="px-5 py-3 rounded-xl bg-white/10 hover:bg-white/15 ring-1 ring-white/20">Show Explorer</button>
          </div>

          <!-- Collapsible Explorer Panel -->
          <div id="explorerPanel" class="mt-6 hidden">
            <!-- Search -->
            <form id="searchForm" class="grid grid-cols-1 md:grid-cols-[1fr_auto] gap-3 md:gap-4">
              <div class="flex items-stretch bg-white/10 rounded-xl ring-1 ring-white/15 focus-within:ring-white/30 transition overflow-hidden">
                <span class="pl-3 md:pl-4 pr-2 grid place-items-center text-white/70">
                  <svg width="18" height="18" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                    <circle cx="11" cy="11" r="7" stroke="currentColor" stroke-width="1.5"/>
                    <path d="M20 20l-3.5-3.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
                  </svg>
                </span>
                <input id="destinationInput" type="text" placeholder="Try: Kyoto, Lisbon, Reykjavik…" class="flex-1 bg-transparent outline-none placeholder:text-white/50 px-2 md:px-3 py-3 md:py-4 text-base md:text-lg" required />
              </div>
              <button class="rounded-xl px-5 md:px-6 py-3 md:py-4 bg-indigo-500 hover:bg-indigo-500/90 text-white font-medium shadow-lg shadow-indigo-900/30">
                Explore
              </button>
            </form>

            <!-- Content Grid -->
            <div class="mt-6 grid grid-cols-1 lg:grid-cols-3 gap-6">
              <div class="lg:col-span-2">
                <div class="flex items-center justify-between mb-3">
                  <h4 class="text-lg font-semibold">Photo Gallery</h4>
                  <div class="text-xs text-white/60" id="photoStatus">Real images load by default.</div>
                </div>
                <div id="photoGrid" class="grid grid-cols-2 md:grid-cols-3 gap-3 md:gap-4"></div>
              </div>
              <div>
                <div class="rounded-2xl p-5 bg-white/5 ring-1 ring-white/10">
                  <div class="flex items-center justify-between">
                    <h4 class="text-lg font-semibold">Weather Peek</h4>
                    <button id="refreshWeatherBtn" class="text-sm px-3 py-1.5 rounded-lg bg-white/10 hover:bg-white/15 ring-1 ring-white/15">Refresh</button>
                  </div>
                  <div id="weatherPanel" class="mt-4 space-y-3">
                    <div class="text-white/70 text-sm">Search a city to see current temperature and wind.</div>
                  </div>
                </div>
              </div>
            </div>

            <!-- Quick Chips -->
            <div class="mt-4 flex flex-wrap gap-2">
              <button data-sample="Tokyo" class="quick px-3 py-1.5 rounded-full bg-white/10 hover:bg-white/15 ring-1 ring-white/15">Tokyo</button>
              <button data-sample="Lisbon" class="quick px-3 py-1.5 rounded-full bg-white/10 hover:bg-white/15 ring-1 ring-white/15">Lisbon</button>
              <button data-sample="Reykjavik" class="quick px-3 py-1.5 rounded-full bg-white/10 hover:bg-white/15 ring-1 ring-white/15">Reykjavik</button>
              <button data-sample="Kyoto" class="quick px-3 py-1.5 rounded-full bg-white/10 hover:bg-white/15 ring-1 ring-white/15">Kyoto</button>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>

  <!-- Lightbox -->
  <div id="lightbox" class="fixed inset-0 hidden items-center justify-center z-[60]">
    <div class="absolute inset-0 bg-black/80" id="lightboxBg"></div>
    <div class="relative max-w-5xl w-[92%] rounded-2xl overflow-hidden ring-1 ring-white/15 lightbox-enter">
      <img id="lightboxImg" src="" alt="Expanded photo" class="w-full max-h-[82vh] object-contain bg-black/40" onerror="this.src=''; this.alt='Image failed to load'; this.style.display='none';">
      <div class="absolute top-3 right-3">
        <button id="lightboxClose" class="px-3 py-2 rounded-lg bg-white/10 hover:bg-white/15 ring-1 ring-white/15">Close</button>
      </div>
    </div>
  </div>

  <script>
    // Elements
    const els = {
      openExplorerBtn: document.getElementById('openExplorerBtn'),
      openExplorerTop: document.getElementById('openExplorerTop'),
      openExplorerMid: document.getElementById('openExplorerMid'),
      explorerPanel: document.getElementById('explorerPanel'),

      // Popular section
      popularGrid: document.getElementById('popularGrid'),
      popularStatus: document.getElementById('popularStatus'),
      popularTitle: document.getElementById('popularTitle'),
      chips: document.querySelectorAll('.chip'),

      // Peek weather
      peekForm: document.getElementById('peekForm'),
      peekCity: document.getElementById('peekCity'),
      peekResult: document.getElementById('peekResult'),

      // Explorer mini-app
      form: document.getElementById('searchForm'),
      input: document.getElementById('destinationInput'),
      photoGrid: document.getElementById('photoGrid'),
      photoStatus: document.getElementById('photoStatus'),
      weatherPanel: document.getElementById('weatherPanel'),
      refreshWeatherBtn: document.getElementById('refreshWeatherBtn'),

      // Lightbox
      lightbox: document.getElementById('lightbox'),
      lightboxImg: document.getElementById('lightboxImg'),
      lightboxBg: document.getElementById('lightboxBg'),
      lightboxClose: document.getElementById('lightboxClose'),
    };

    const state = { currentCity: '' };

    // Basic helpers
    function setPhotoStatus(text) { if (els.photoStatus) els.photoStatus.textContent = text; }
    function createSkeletonCards(count = 6) {
      const frag = document.createDocumentFragment();
      for (let i = 0; i < count; i++) {
        const d = document.createElement('div');
        d.className = 'aspect-[4/3] rounded-xl bg-white/5 ring-1 ring-white/10 animate-pulse';
        frag.appendChild(d);
      }
      return frag;
    }

    // Lightbox controls
    function openLightbox(url) {
      els.lightboxImg.style.display = 'block';
      els.lightboxImg.src = url;
      els.lightbox.classList.remove('hidden');
      els.lightbox.classList.add('flex');
    }
    function closeLightbox() {
      els.lightboxImg.src = '';
      els.lightbox.classList.add('hidden');
      els.lightbox.classList.remove('flex');
    }
    els.lightboxBg.addEventListener('click', closeLightbox);
    els.lightboxClose.addEventListener('click', closeLightbox);
    document.addEventListener('keydown', (e) => { if (e.key === 'Escape') closeLightbox(); });

    // Wikipedia/Commons photo search (no key)
    async function searchWikipediaPhotos(place) {
      // 1) Find page
      const s = await fetch(`https://en.wikipedia.org/w/api.php?action=query&format=json&origin=*&list=search&srlimit=1&srsearch=${encodeURIComponent(place)}`);
      if (!s.ok) throw new Error('Wikipedia search error');
      const sData = await s.json();
      const page = sData?.query?.search?.[0];
      if (!page) return [];
      // 2) Get images on page
      const iRes = await fetch(`https://en.wikipedia.org/w/api.php?action=query&format=json&origin=*&prop=images&pageids=${page.pageid}`);
      if (!iRes.ok) throw new Error('Wikipedia images error');
      const iData = await iRes.json();
      const images = iData?.query?.pages?.[page.pageid]?.images || [];
      // 3) Resolve to URLs
      const results = [];
      for (const img of images.slice(0, 18)) {
        const title = img.title;
        if (!/^File:/i.test(title)) continue;
        const infoRes = await fetch(`https://en.wikipedia.org/w/api.php?action=query&format=json&origin=*&prop=imageinfo&iiprop=url&titles=${encodeURIComponent(title)}`);
        if (!infoRes.ok) continue;
        const infoData = await infoRes.json();
        const pages = infoData?.query?.pages || {};
        const first = pages[Object.keys(pages)[0]];
        const url = first?.imageinfo?.[0]?.url || '';
        if (!url) continue;
        const lower = url.toLowerCase();
        if (lower.endsWith('.svg') || /icon|logo|coat_of_arms|flag|map/i.test(lower)) continue;
        results.push({ url, alt: `${place} photo` });
        if (results.length >= 9) break;
      }
      return results;
    }

    // Open-Meteo quick weather (no key)
    async function quickWeather(city) {
      const geo = await fetch(`https://geocoding-api.open-meteo.com/v1/search?name=${encodeURIComponent(city)}&count=1&language=en&format=json`);
      if (!geo.ok) throw new Error('Geocoding failed');
      const gj = await geo.json();
      if (!gj?.results?.length) throw new Error('City not found');
      const { latitude, longitude, name, country } = gj.results[0];
      const wx = await fetch(`https://api.open-meteo.com/v1/forecast?latitude=${latitude}&longitude=${longitude}&current_weather=true`);
      if (!wx.ok) throw new Error('Weather failed');
      const wj = await wx.json();
      const cw = wj.current_weather || {};
      return { name, country, temp: cw.temperature, wind: cw.windspeed };
    }

    // Popular destination loader
    async function loadPopular(place) {
      els.popularTitle.textContent = `Photos • ${place}`;
      els.popularGrid.innerHTML = '';
      els.popularGrid.appendChild(createSkeletonCards(6));
      els.popularStatus.textContent = 'Fetching photos...';
      try {
        const photos = await searchWikipediaPhotos(place);
        renderGrid(els.popularGrid, photos, place);
        els.popularStatus.textContent = `Showing photos for “${place}”`;
      } catch (e) {
        els.popularGrid.innerHTML = '';
        const d = document.createElement('div');
        d.className = 'col-span-2 md:col-span-3 rounded-xl bg-white/5 ring-1 ring-white/10 p-6 text-center text-white/70';
        d.textContent = 'Could not load photos. Try another destination.';
        els.popularGrid.appendChild(d);
        els.popularStatus.textContent = 'Error fetching photos.';
      }
    }

    function renderGrid(container, photos, place) {
      container.innerHTML = '';
      if (!photos.length) {
        const d = document.createElement('div');
        d.className = 'col-span-2 md:col-span-3 rounded-xl bg-white/5 ring-1 ring-white/10 p-6 text-center text-white/70';
        d.textContent = 'No photos found.';
        container.appendChild(d);
        return;
      }
      const frag = document.createDocumentFragment();
      photos.forEach(p => {
        const item = document.createElement('div');
        item.className = 'group relative aspect-[4/3] overflow-hidden rounded-xl ring-1 ring-white/10 bg-black/20';
        item.innerHTML = `
          <img src="${p.url}" alt="${p.alt}" class="w-full h-full object-cover transition duration-300 group-hover:scale-[1.03]" onerror="this.src=''; this.alt='Image failed to load'; this.style.display='none';">
          <div class="absolute inset-0 bg-gradient-to-t from-black/40 via-black/5 to-transparent"></div>
          <button class="absolute bottom-2 right-2 px-2.5 py-1.5 rounded-lg bg-white/10 hover:bg-white/15 ring-1 ring-white/15 text-xs">View</button>
        `;
        item.querySelector('button').addEventListener('click', () => openLightbox(p.url));
        frag.appendChild(item);
      });
      container.appendChild(frag);
    }

    // Explorer mini-app search
    async function doSearch(city) {
      if (!city) return;
      state.currentCity = city;
      if (els.photoGrid) {
        els.photoGrid.innerHTML = '';
        els.photoGrid.appendChild(createSkeletonCards(6));
        setPhotoStatus('Searching photos...');
      }
      if (els.weatherPanel) {
        els.weatherPanel.innerHTML = '';
        const loading = document.createElement('div');
        loading.className = 'rounded-xl bg-white/5 ring-1 ring-white/10 p-4 text-white/80';
        loading.textContent = 'Fetching weather...';
        els.weatherPanel.appendChild(loading);
      }
      // Photos
      try {
        const photos = await searchWikipediaPhotos(city);
        renderGrid(els.photoGrid, photos, city);
        setPhotoStatus(`Showing photos for “${city}”`);
      } catch {
        setPhotoStatus('Could not load photos.');
        els.photoGrid.innerHTML = '';
      }
      // Weather
      try {
        const w = await quickWeather(city);
        renderWeatherPanel(w);
      } catch {
        els.weatherPanel.innerHTML = '';
        const d = document.createElement('div');
        d.className = 'rounded-xl bg-white/5 ring-1 ring-white/10 p-4 text-white/70';
        d.textContent = 'Could not fetch weather right now.';
        els.weatherPanel.appendChild(d);
      }
    }

    function renderWeatherPanel(data) {
      els.weatherPanel.innerHTML = '';
      const card = document.createElement('div');
      card.className = 'rounded-xl bg-gradient-to-br from-indigo-500/30 to-cyan-500/20 ring-1 ring-white/15 p-4';
      card.innerHTML = `
        <div class="text-sm text-white/70">${data.name}, ${data.country}</div>
        <div class="mt-1 text-3xl font-semibold">${Math.round(data.temp)}°C</div>
        <div class="text-white/80">Wind: ${Math.round(data.wind)} km/h</div>
      `;
      els.weatherPanel.appendChild(card);
    }

    // Events
    [els.openExplorerBtn, els.openExplorerTop, els.openExplorerMid].forEach(btn => {
      if (!btn) return;
      btn.addEventListener('click', () => {
        els.explorerPanel.classList.remove('hidden');
        document.querySelector('#explore')?.scrollIntoView({ behavior: 'smooth', block: 'start' });
      });
    });

    if (els.peekForm) {
      els.peekForm.addEventListener('submit', async (e) => {
        e.preventDefault();
        const city = els.peekCity.value.trim();
        if (!city) return;
        els.peekResult.textContent = 'Checking…';
        try {
          const w = await quickWeather(city);
          els.peekResult.textContent = `${w.name}, ${w.country}: ${Math.round(w.temp)}°C, wind ${Math.round(w.wind)} km/h`;
        } catch {
          els.peekResult.textContent = 'Could not fetch weather. Try another city.';
        }
      });
    }

    if (els.form) {
      els.form.addEventListener('submit', (e) => {
        e.preventDefault();
        const city = els.input.value.trim();
        if (!city) return;
        doSearch(city);
      });
    }

    if (els.refreshWeatherBtn) {
      els.refreshWeatherBtn.addEventListener('click', () => {
        if (state.currentCity) doSearch(state.currentCity);
      });
    }

    document.querySelectorAll('.quick').forEach(q => {
      q.addEventListener('click', () => {
        const city = q.getAttribute('data-sample');
        els.input.value = city;
        doSearch(city);
      });
    });

    els.chips.forEach(chip => {
      chip.addEventListener('click', () => {
        const place = chip.getAttribute('data-place');
        loadPopular(place);
      });
    });

    // Init with a friendly default in popular previews
    loadPopular('Japan');
  </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'983eef5272d2f3bc',t:'MTc1ODY4MTgxMy4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
