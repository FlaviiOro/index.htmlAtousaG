<!-- UPDATE THE STYLE TAG WITH THESE POLISHED SECTIONS -->
<style>
  /* PREMIUM DISCO VENUE STRIP */
  .venues-container {
    border-top: 1px solid rgba(196, 162, 74, 0.15);
    border-bottom: 1px solid rgba(196, 162, 74, 0.15);
    background: #09090b;
    padding: 60px 24px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .venues-brand-header {
    margin-bottom: 32px;
  }

  .venues-brand-header h2 {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 32px;
    letter-spacing: 0.1em;
    color: var(--white);
    line-height: 1;
    margin-bottom: 6px;
  }

  .venues-brand-sub {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.3em;
    color: var(--gold);
    text-transform: uppercase;
  }

  .venues-grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 16px 36px;
    max-width: 900px;
    margin: 0 auto;
  }

  .venue-tag {
    font-family: 'Space Mono', monospace;
    font-size: 13px;
    font-weight: 500;
    color: var(--bright);
    letter-spacing: 0.05em;
    text-transform: uppercase;
    transition: all 0.3s cubic-bezier(0.25, 1, 0.5, 1);
    cursor: default;
    position: relative;
    padding: 4px 0;
  }

  /* Disco Laser Light-Beam Hover */
  .venue-tag:hover {
    color: var(--gold2);
    text-shadow: 0 0 12px rgba(223, 192, 122, 0.6);
    transform: translateY(-1px);
  }

  /* HIGH-END EDITORIAL FOOTER */
  .premium-footer {
    padding: 90px 24px;
    text-align: center;
    background: var(--black);
  }

  .footer-eyebrow {
    font-family: 'Space Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.4em;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 16px;
    display: block;
  }

  .footer-headline {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: clamp(24px, 4vw, 36px);
    color: var(--white);
    margin-bottom: 32px;
    line-height: 1.2;
  }

  .footer-btn {
    display: inline-block;
    padding: 16px 42px;
    border: 1px solid var(--gold);
    color: var(--white);
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    text-decoration: none;
    background: transparent;
    transition: all 0.4s cubic-bezier(0.25, 1, 0.5, 1);
    position: relative;
  }

  .footer-btn:hover {
    background: var(--gold);
    color: var(--black);
    box-shadow: 0 0 25px rgba(196, 162, 74, 0.25);
    transform: translateY(-2px);
  }
</style>

<!-- DISCO VENUES STRIP -->
<div class="venues-container">
  <div class="venues-brand-header">
    <h2>ATOUSA G</h2>
    <div class="venues-brand-sub">House of G$ · A Line Called K</div>
  </div>
  
  <div class="venues-grid">
    <span class="venue-tag">Halcyon · SF</span>
    <span class="venue-tag">Do Not Sit On The Furniture · Miami</span>
    <span class="venue-tag">Great Northern · SF</span>
    <span class="venue-tag">Monarch · SF</span>
    <span class="venue-tag">BPM Festival</span>
    <span class="venue-tag">Sunset Campout</span>
    <span class="venue-tag">SXM Festival</span>
    <span class="venue-tag">Symbiosis</span>
  </div>
</div>

<!-- POLISHED FOOTER -->
<div class="premium-footer">
  <span class="footer-eyebrow">Inquiries &amp; Bookings</span>
  <p class="footer-headline">Press collaborations, styling requests &amp; archive access.</p>
  <a href="mailto:press@atousag.com" class="footer-btn">Contact Representative</a>
</div>
<div class="bottom-rule"></div>

<!-- LIGHTBOX -->
<div id="lightbox">
  <div class="lb-inner">
    <img id="lb-img" src="" alt=""/>
    <div class="lb-body">
      <span class="lb-meta" id="lb-meta"></span>
      <p class="lb-caption" id="lb-caption"></p>
    </div>
    <button class="lb-close" onclick="closeLightbox()">Close ✕</button>
  </div>
</div>

<script>
  // SMOOTH FILTERS
  document.querySelectorAll('.filter-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      const f = btn.dataset.filter;
      
      document.querySelectorAll('.card').forEach(card => {
        if (f === 'all' || card.dataset.type === f) {
          card.classList.remove('hidden');
        } else {
          card.classList.add('hidden');
        }
      });
    });
  });

  // LIGHTBOX OPEN WITH FADE
  document.querySelectorAll('.card').forEach(card => {
    card.addEventListener('click', () => {
      if (card.classList.contains('hidden')) return;
      
      const lb = document.getElementById('lightbox');
      document.getElementById('lb-img').src = card.dataset.src;
      document.getElementById('lb-meta').textContent = card.dataset.tag + ' · ' + card.dataset.venue;
      document.getElementById('lb-caption').textContent = '"' + card.dataset.caption + '"';
      lb.classList.add('open');
      document.body.style.overflow = 'hidden';
    });
  });

  // LIGHTBOX CLOSE WITH FADE
  function closeLightbox() {
    document.getElementById('lightbox').classList.remove('open');
    document.body.style.overflow = '';
  }
  document.getElementById('lightbox').addEventListener('click', function(e) {
    if (e.target === this) closeLightbox();
  });
  document.addEventListener('keydown', e => { if (e.key === 'Escape') closeLightbox(); });
</script>
</body>
</html>
