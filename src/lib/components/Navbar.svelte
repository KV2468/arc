<script>
  import { onMount } from 'svelte';

  let scrolled = $state(false);
  let mobileOpen = $state(false);

  onMount(() => {
    const handleScroll = () => { scrolled = window.scrollY > 50; };
    window.addEventListener('scroll', handleScroll, { passive: true });
    return () => window.removeEventListener('scroll', handleScroll);
  });

  const navLinks = [
    { href: '#about',        label: 'About' },
    { href: '#achievements', label: 'Achievements' },
    { href: '#team',         label: 'Team' },
    { href: '#gallery',      label: 'Gallery' },
    { href: '#videos',       label: 'Videos' },
    { href: '#contact',      label: 'Contact' },
  ];

  function closeMenu() { mobileOpen = false; }
</script>

<nav class="navbar" class:scrolled>
  <div class="nav-inner container">
    <!-- Logo -->
    <a href="#hero" class="nav-logo" on:click={closeMenu}>
      <div class="logo-icon">
        <svg viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <path d="M16 2L20 12L16 10L12 12L16 2Z" fill="url(#lg1)"/>
          <path d="M16 10L20 12L22 28L16 24L10 28L12 12L16 10Z" fill="url(#lg2)"/>
          <path d="M10 28L13 22L16 24L16 30L10 28Z" fill="#F0C040"/>
          <path d="M22 28L19 22L16 24L16 30L22 28Z" fill="#F0C040"/>
          <defs>
            <linearGradient id="lg1" x1="16" y1="2" x2="16" y2="12" gradientUnits="userSpaceOnUse">
              <stop stop-color="#FFD700"/>
              <stop offset="1" stop-color="#F5A623"/>
            </linearGradient>
            <linearGradient id="lg2" x1="16" y1="10" x2="16" y2="28" gradientUnits="userSpaceOnUse">
              <stop stop-color="#9B67E8"/>
              <stop offset="1" stop-color="#4A1A8C"/>
            </linearGradient>
          </defs>
        </svg>
      </div>
      <div class="logo-text">
        <span class="logo-main">Matador Rocketry</span>
        <span class="logo-sub">MVHS • ARC</span>
      </div>
    </a>

    <!-- Desktop Links -->
    <ul class="nav-links" role="list">
      {#each navLinks as link}
        <li>
          <a href={link.href} class="nav-link" on:click={closeMenu}>{link.label}</a>
        </li>
      {/each}
    </ul>

    <!-- CTA -->
    <a href="#contact" class="btn btn-primary nav-cta" on:click={closeMenu} id="nav-contact-btn">
      Join Us
    </a>

    <!-- Hamburger -->
    <button
      class="hamburger"
      class:open={mobileOpen}
      on:click={() => mobileOpen = !mobileOpen}
      aria-label="Toggle navigation menu"
      aria-expanded={mobileOpen}
    >
      <span></span><span></span><span></span>
    </button>
  </div>

  <!-- Mobile Menu -->
  {#if mobileOpen}
    <div class="mobile-menu" role="dialog" aria-label="Navigation menu">
      <ul role="list">
        {#each navLinks as link}
          <li>
            <a href={link.href} class="mobile-link" on:click={closeMenu}>{link.label}</a>
          </li>
        {/each}
        <li>
          <a href="#contact" class="btn btn-primary mobile-cta" on:click={closeMenu}>Join Us</a>
        </li>
      </ul>
    </div>
  {/if}
</nav>

<style>
  .navbar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1000;
    padding: 1.25rem 0;
    transition: all 0.35s ease;
  }

  .navbar.scrolled {
    background: rgba(10, 3, 20, 0.92);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    padding: 0.8rem 0;
    border-bottom: 1px solid rgba(107, 53, 196, 0.25);
    box-shadow: 0 4px 30px rgba(0,0,0,0.4);
  }

  .nav-inner {
    display: flex;
    align-items: center;
    gap: 2rem;
  }

  /* Logo */
  .nav-logo {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    text-decoration: none;
    flex-shrink: 0;
  }

  .logo-icon {
    width: 36px;
    height: 36px;
    filter: drop-shadow(0 0 8px rgba(240,192,64,0.5));
    transition: filter 0.3s ease;
  }
  .nav-logo:hover .logo-icon { filter: drop-shadow(0 0 14px rgba(240,192,64,0.9)); }

  .logo-text { display: flex; flex-direction: column; line-height: 1.1; }
  .logo-main {
    font-family: 'Outfit', sans-serif;
    font-size: 1rem;
    font-weight: 800;
    color: #fff;
    letter-spacing: 0.01em;
  }
  .logo-sub {
    font-family: 'Outfit', sans-serif;
    font-size: 0.65rem;
    font-weight: 600;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--yellow-gold, #F0C040);
  }

  /* Nav links */
  .nav-links {
    display: flex;
    gap: 0.25rem;
    list-style: none;
    margin-left: auto;
  }

  .nav-link {
    font-family: 'Outfit', sans-serif;
    font-size: 0.9rem;
    font-weight: 500;
    color: rgba(255,255,255,0.8);
    text-decoration: none;
    padding: 0.5rem 0.85rem;
    border-radius: 8px;
    transition: all 0.2s ease;
    position: relative;
  }
  .nav-link::after {
    content: '';
    position: absolute;
    bottom: 4px;
    left: 50%;
    right: 50%;
    height: 2px;
    background: var(--yellow-gold, #F0C040);
    border-radius: 1px;
    transition: all 0.25s ease;
  }
  .nav-link:hover { color: #fff; }
  .nav-link:hover::after { left: 0.85rem; right: 0.85rem; }

  /* CTA */
  .nav-cta {
    padding: 0.55rem 1.4rem;
    font-size: 0.88rem;
    white-space: nowrap;
  }

  /* Hamburger */
  .hamburger {
    display: none;
    flex-direction: column;
    gap: 5px;
    background: none;
    border: none;
    cursor: pointer;
    padding: 0.4rem;
    margin-left: auto;
  }
  .hamburger span {
    display: block;
    width: 24px;
    height: 2px;
    background: #fff;
    border-radius: 2px;
    transition: all 0.3s ease;
    transform-origin: center;
  }
  .hamburger.open span:nth-child(1) { transform: rotate(45deg) translate(5px, 5px); }
  .hamburger.open span:nth-child(2) { opacity: 0; transform: scaleX(0); }
  .hamburger.open span:nth-child(3) { transform: rotate(-45deg) translate(5px, -5px); }

  /* Mobile menu */
  .mobile-menu {
    background: rgba(10, 3, 20, 0.97);
    backdrop-filter: blur(20px);
    border-top: 1px solid rgba(107, 53, 196, 0.25);
    padding: 1rem 1.5rem 1.5rem;
    animation: slideDown 0.3s ease;
  }
  .mobile-menu ul { list-style: none; display: flex; flex-direction: column; gap: 0.25rem; }
  .mobile-link {
    display: block;
    font-family: 'Outfit', sans-serif;
    font-size: 1.1rem;
    font-weight: 500;
    color: rgba(255,255,255,0.85);
    text-decoration: none;
    padding: 0.8rem 1rem;
    border-radius: 8px;
    transition: all 0.2s ease;
  }
  .mobile-link:hover { background: rgba(107,53,196,0.2); color: #fff; }
  .mobile-cta { margin-top: 0.5rem; text-align: center; }

  @keyframes slideDown {
    from { opacity: 0; transform: translateY(-8px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @media (max-width: 900px) {
    .nav-links, .nav-cta { display: none; }
    .hamburger { display: flex; }
  }
</style>
