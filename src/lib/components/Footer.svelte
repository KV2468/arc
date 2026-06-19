<footer class="footer">
  <div class="footer-glow"></div>
  <div class="container footer-inner">
    <div class="footer-brand">
      <div class="footer-logo-row">
        <svg width="28" height="28" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <path d="M16 2L20 12L16 10L12 12L16 2Z" fill="url(#flg1)"/>
          <path d="M16 10L20 12L22 28L16 24L10 28L12 12L16 10Z" fill="url(#flg2)"/>
          <path d="M10 28L13 22L16 24L16 30L10 28Z" fill="#F0C040"/>
          <path d="M22 28L19 22L16 24L16 30L22 28Z" fill="#F0C040"/>
          <defs>
            <linearGradient id="flg1" x1="16" y1="2" x2="16" y2="12" gradientUnits="userSpaceOnUse">
              <stop stop-color="#FFD700"/>
              <stop offset="1" stop-color="#F5A623"/>
            </linearGradient>
            <linearGradient id="flg2" x1="16" y1="10" x2="16" y2="28" gradientUnits="userSpaceOnUse">
              <stop stop-color="#9B67E8"/>
              <stop offset="1" stop-color="#4A1A8C"/>
            </linearGradient>
          </defs>
        </svg>
        <span class="footer-name">Matador Rocketry</span>
      </div>
      <p class="footer-desc">Monta Vista High School's competitive rocketry team, representing Cupertino in the American Rocketry Challenge.</p>
      <div class="footer-socials">
        <a href="mailto:matadorrocketry@mvhs.edu" class="social-pill" id="footer-email-link" aria-label="Email us">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
          Email Us
        </a>
        <a href="https://www.rocketrychallenge.org" target="_blank" rel="noopener noreferrer" class="social-pill" id="footer-arc-link" aria-label="ARC Website">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><circle cx="12" cy="12" r="10"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/><path d="M2 12h20"/></svg>
          ARC
        </a>
      </div>
    </div>

    <div class="footer-links-col">
      <h4 class="footer-col-title">Navigate</h4>
      <ul role="list">
        <li><a href="#about">About</a></li>
        <li><a href="#achievements">Achievements</a></li>
        <li><a href="#team">Team</a></li>
        <li><a href="#gallery">Gallery</a></li>
        <li><a href="#videos">Videos</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </div>

    <div class="footer-links-col">
      <h4 class="footer-col-title">Resources</h4>
      <ul role="list">
        <li><a href="https://www.rocketrychallenge.org" target="_blank" rel="noopener noreferrer">ARC Official</a></li>
        <li><a href="https://www.nar.org" target="_blank" rel="noopener noreferrer">NAR</a></li>
        <li><a href="https://mvhs.fuhsd.org" target="_blank" rel="noopener noreferrer">Monta Vista HS</a></li>
      </ul>
    </div>
  </div>

  <div class="footer-bottom container">
    <p>© {new Date().getFullYear()} Matador Rocketry · Monta Vista High School · Cupertino, CA</p>
    <p class="footer-tagline">🚀 Ad Astra</p>
  </div>
</footer>

<style>
  .footer {
    background: linear-gradient(180deg, #080212 0%, #0A0314 100%);
    border-top: 1px solid rgba(107, 53, 196, 0.2);
    padding: 4rem 0 0;
    position: relative;
    overflow: hidden;
  }

  .footer-glow {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 600px;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(240,192,64,0.6), transparent);
  }

  .footer-inner {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr;
    gap: 3rem;
    padding-bottom: 3rem;
  }

  .footer-logo-row {
    display: flex;
    align-items: center;
    gap: 0.6rem;
    margin-bottom: 0.9rem;
  }
  .footer-name {
    font-family: 'Outfit', sans-serif;
    font-size: 1.1rem;
    font-weight: 800;
    color: #fff;
  }

  .footer-desc {
    color: rgba(196, 160, 245, 0.7);
    font-size: 0.9rem;
    line-height: 1.65;
    max-width: 300px;
    margin-bottom: 1.25rem;
  }

  .footer-socials {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
  }

  .social-pill {
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    padding: 0.45rem 0.9rem;
    border-radius: 99px;
    border: 1px solid rgba(155, 103, 232, 0.35);
    color: rgba(196, 160, 245, 0.9);
    font-size: 0.82rem;
    font-family: 'Outfit', sans-serif;
    font-weight: 500;
    text-decoration: none;
    transition: all 0.2s ease;
  }
  .social-pill:hover {
    border-color: var(--yellow-gold, #F0C040);
    color: var(--yellow-gold, #F0C040);
    background: rgba(240,192,64,0.08);
  }

  .footer-col-title {
    font-family: 'Outfit', sans-serif;
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--yellow-gold, #F0C040);
    margin-bottom: 1rem;
  }
  .footer-links-col ul { list-style: none; display: flex; flex-direction: column; gap: 0.55rem; }
  .footer-links-col a {
    color: rgba(196, 160, 245, 0.7);
    text-decoration: none;
    font-size: 0.9rem;
    transition: color 0.2s ease;
  }
  .footer-links-col a:hover { color: #fff; }

  .footer-bottom {
    border-top: 1px solid rgba(107, 53, 196, 0.15);
    padding: 1.5rem 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 1rem;
    flex-wrap: wrap;
  }
  .footer-bottom p {
    font-size: 0.82rem;
    color: rgba(196, 160, 245, 0.5);
  }
  .footer-tagline { font-size: 0.9rem !important; color: rgba(240,192,64,0.7) !important; }

  @media (max-width: 768px) {
    .footer-inner {
      grid-template-columns: 1fr 1fr;
      gap: 2rem;
    }
    .footer-brand { grid-column: 1 / -1; }
    .footer-bottom { flex-direction: column; text-align: center; }
  }
  @media (max-width: 500px) {
    .footer-inner { grid-template-columns: 1fr; }
  }
</style>
