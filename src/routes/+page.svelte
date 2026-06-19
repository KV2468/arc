<script>
  import { onMount } from "svelte";

  // ─── DATA ───────────────────────────────────────────────────────────────────
  const achievements = [
    {
      year: "2024",
      title: "ARC National Finals Qualifier",
      desc: "Qualified for the American Rocketry Challenge National Finals in Virginia, competing among the top 100 teams in the nation.",
      icon: "🏆",
    },
    {
      year: "2024",
      title: "Regional Championship — 2nd Place",
      desc: "Achieved second place at the Western Regional Qualifier with an altitude score within 3 feet of target.",
      icon: "🥈",
    },
    {
      year: "2023",
      title: "Perfect Flight Award",
      desc: "Received the Perfect Flight Award for achieving an altitude within 1% of the target and a flight time within 0.5 seconds.",
      icon: "🎯",
    },
    {
      year: "2023",
      title: "ARC Regional Qualifier",
      desc: "First-ever qualification to the Regional stage in the club's history, placing top 20 at the Pacific Southwest Qualifier.",
      icon: "🚀",
    },
    {
      year: "2022",
      title: "MVHS STEM Showcase Winner",
      desc: "Won the Monta Vista STEM Showcase for outstanding engineering presentation and rocket design innovation.",
      icon: "🌟",
    },
    {
      year: "2022",
      title: "Founded Matador Rocketry",
      desc: "Established the Matador Rocketry division of the MVHS Rocketry Club, dedicated to ARC competition.",
      icon: "🎉",
    },
  ];

  const teamMembers = [
    {
      name: "Krish Vimalkumar",
      title: "Team Captain",
    },
    {
      name: "Ashwin Rajkumar",
      title: "Member",
    },
    {
      name: "Qicheng (Anthony) Lin",
      title: "Member",
    },
    {
      name: "Ryan Kim",
      title: "Member",
    },
    {
      name: "Derek Li",
      title: "Member",
    },
    {
      name: "Rohan Agarwal",
      title: "Member",
    },
    {
      name: "Advaith Prabhu",
      title: "Member",
    },
    {
      name: "Chris Ahn",
      title: "Member",
    },
  ];

  const galleryImages = [
    {
      src: "/dark-purple-placeholder.svg",
      alt: "Team member assembling rocket at competition",
    },
    {
      src: "/dark-purple-placeholder.svg",
      alt: "Rocket components laid out before launch",
    },
    {
      src: "/dark-purple-placeholder.svg",
      alt: "Team carrying rocket to launch pad",
    },
    {
      src: "/dark-purple-placeholder.svg",
      alt: "Close-up of rocket motor section",
    },
    {
      src: "/dark-purple-placeholder.svg",
      alt: "Team discussing launch strategy",
    },
    {
      src: "/dark-purple-placeholder.svg",
      alt: "Rocket on launch rail ready for flight",
    },
    {
      src: "/dark-purple-placeholder.svg",
      alt: "Team inspecting rocket after recovery",
    },
    {
      src: "/dark-purple-placeholder.svg",
      alt: "Recovered rocket body section on field",
    },
    {
      src: "/dark-purple-placeholder.svg",
      alt: "Team at ARC competition site",
    },
    {
      src: "/dark-purple-placeholder.svg",
      alt: "Matador Rocketry team group photo",
    },
    {
      src: "/dark-purple-placeholder.svg",
      alt: "Rocket airframe detail",
    },
    {
      src: "/dark-purple-placeholder.svg",
      alt: "Team working on rocket at launch site",
    },
  ];

  const videos = [
    {
      id: "launch-1",
      src: "/media/converted/IMG_3150.mp4",
    },
    {
      id: "launch-2",
      src: "/media/converted/IMG_3156.mp4",
    },
    {
      id: "launch-3",
      src: "/media/converted/IMG_3157.mp4",
    },
    {
      id: "flight-4",
      src: "/media/converted/IMG_3161.mp4",
    },
    {
      id: "flight-5",
      src: "/media/converted/IMG_3162.mp4",
    },
    {
      id: "flight-6",
      src: "/media/converted/IMG_4724.mp4",
    },
  ];

  // ─── INTERSECTION OBSERVER FOR FADE-IN ──────────────────────────────────────
  onMount(() => {
    const els = document.querySelectorAll(".reveal");
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((e) => {
          if (e.isIntersecting) {
            e.target.classList.add("visible");
            observer.unobserve(e.target);
          }
        });
      },
      { threshold: 0.12, rootMargin: "0px 0px -40px 0px" },
    );
    els.forEach((el) => observer.observe(el));
    return () => observer.disconnect();
  });

  // ─── CONTACT FORM ────────────────────────────────────────────────────────────
  let formName = $state("");
  let formEmail = $state("");
  let formMessage = $state("");
  let formStatus = $state(null); // null | 'success' | 'error'

  function handleSubmit(e) {
    e.preventDefault();
    if (!formName || !formEmail || !formMessage) {
      formStatus = "error";
      return;
    }
    window.location.href = `mailto:matadorrocketry@mvhs.edu?subject=Message from ${encodeURIComponent(formName)}&body=${encodeURIComponent(formMessage + "\n\nFrom: " + formName + "\nEmail: " + formEmail)}`;
    formStatus = "success";
    formName = "";
    formEmail = "";
    formMessage = "";
  }

  // Active gallery image
  let activeGallery = $state(0);
</script>

<svelte:head>
  <title>Matador Rocketry | Monta Vista High School</title>
</svelte:head>

<!-- ═══════════════════════════════════════════════════════════════
     HERO
════════════════════════════════════════════════════════════════ -->
<section id="hero" class="hero stars-bg">
  <div class="hero-bg-img" aria-hidden="true"></div>
  <div class="hero-overlay" aria-hidden="true"></div>

  <!-- Floating orbs -->
  <div class="orb orb-1" aria-hidden="true"></div>
  <div class="orb orb-2" aria-hidden="true"></div>
  <div class="orb orb-3" aria-hidden="true"></div>

  <div class="container hero-content">
    <div class="hero-badge">
      <span class="badge-dot"></span>
      American Rocketry Challenge 2024–2025
    </div>

    <h1 class="hero-title">
      <span class="hero-line-1">Matador</span>
      <span class="hero-line-2">Rocketry</span>
    </h1>

    <p class="hero-subtitle">
      Monta Vista High School's premier competitive rocketry team — engineering
      precision, fueling ambition, reaching for the stars.
    </p>

    <div class="hero-btns">
      <a href="#about" class="btn btn-primary" id="hero-learn-btn"
        >Explore Our Story</a
      >
      <a href="#contact" class="btn btn-outline" id="hero-join-btn"
        >Join the Team</a
      >
    </div>

    <div class="hero-stats">
      <div class="stat-item">
        <span class="stat-num">2</span>
        <span class="stat-label">Years Competing</span>
      </div>
      <div class="stat-divider" aria-hidden="true"></div>
      <div class="stat-item">
        <span class="stat-num">8+</span>
        <span class="stat-label">Team Members</span>
      </div>
    </div>
  </div>

  <div class="hero-scroll-hint" aria-hidden="true">
    <div class="scroll-line"></div>
    <span>Scroll</span>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════════
     ABOUT
════════════════════════════════════════════════════════════════ -->
<section id="about" class="about-section">
  <div class="container about-grid">
    <div class="about-img-col reveal">
      <div class="about-img-wrapper">
        <img
          src="/dark-purple-placeholder.svg"
          alt="Matador Rocketry team in the workshop building their competition rocket"
          loading="lazy"
        />
        <div class="about-img-badge glass-card">
          <span class="badge-emoji">🚀</span>
          <div>
            <strong>ARC Competitors</strong>
            <p>Since 2022</p>
          </div>
        </div>
      </div>
    </div>

    <div class="about-text-col reveal">
      <span class="section-label">Who We Are</span>
      <h2 class="section-title">
        Launching Dreams from <span>Cupertino</span>
      </h2>
      <div class="divider"></div>
      <p class="section-subtitle" style="max-width:100%">
        Matador Rocketry is the competitive division of the <strong
          >Monta Vista High School Rocketry Club</strong
        >, based in Cupertino, CA. We design, build, and fly model rockets that
        meet the strict altitude and flight-time requirements of the
        <strong>American Rocketry Challenge (ARC)</strong> — the world's largest student
        rocket contest.
      </p>
      <p class="about-body-text">
        Our team brings together students from all grade levels who share a
        passion for STEM, engineering, and the thrill of watching a rocket
        pierce the sky. We use industry-standard tools like OpenRocket, work
        with real composite materials, and develop skills that carry into
        aerospace careers.
      </p>
      <div class="about-tags">
        <span class="tag">OpenRocket Simulation</span>
        <span class="tag">Composite Airframes</span>
        <span class="tag">Avionics</span>
        <span class="tag">Recovery Systems</span>
        <span class="tag">NAR Safety</span>
        <span class="tag">TARC / ARC</span>
      </div>
      <a
        href="https://www.rocketrychallenge.org"
        target="_blank"
        rel="noopener noreferrer"
        class="btn btn-outline"
        id="about-arc-btn"
        style="margin-top:1.5rem;"
      >
        Learn About ARC →
      </a>
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════════
     ACHIEVEMENTS
════════════════════════════════════════════════════════════════ -->
<!-- <section id="achievements" class="achievements-section stars-bg"> -->
<!--   <div class="container"> -->
<!--     <div class="section-header reveal"> -->
<!--       <span class="section-label">Our Track Record</span> -->
<!--       <h2 class="section-title">Built to <span>Win</span></h2> -->
<!--       <div class="divider"></div> -->
<!--       <p class="section-subtitle"> -->
<!--         From our founding to competing on the national stage — here's how far -->
<!--         we've come. -->
<!--       </p> -->
<!--     </div> -->
<!---->
<!--     <div class="achievements-grid"> -->
<!--       {#each achievements as ach, i} -->
<!--         <article -->
<!--           class="achievement-card glass-card reveal" -->
<!--           style="--delay:{i * 0.08}s" -->
<!--           id="achievement-{i}" -->
<!--         > -->
<!--           <div class="ach-top"> -->
<!--             <span class="ach-icon">{ach.icon}</span> -->
<!--             <span class="ach-year">{ach.year}</span> -->
<!--           </div> -->
<!--           <h3 class="ach-title">{ach.title}</h3> -->
<!--           <p class="ach-desc">{ach.desc}</p> -->
<!--         </article> -->
<!--       {/each} -->
<!--     </div> -->
<!--   </div> -->
<!-- </section> -->
<!---->
<!-- ═══════════════════════════════════════════════════════════════
     TEAM
════════════════════════════════════════════════════════════════ -->
<section id="team" class="team-section">
  <div class="container">
    <div class="section-header reveal">
      <span class="section-label">The Crew</span>
      <h2 class="section-title">Meet Our <span>Team</span></h2>
      <div class="divider"></div>
      <p class="section-subtitle">
        The brilliant minds behind every rocket we launch — engineers, analysts,
        builders, and leaders.
      </p>
    </div>

    <div class="team-grid">
      {#each teamMembers as member, i}
        <article
          class="member-card glass-card reveal"
          style="--delay:{i * 0.07}s"
          id="member-{i}"
        >
          <div class="member-info">
            <div class="member-grade">MVHS Rocketry</div>
            <h3 class="member-name">{member.name}</h3>
            <p class="member-title">{member.title}</p>
          </div>
        </article>
      {/each}
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════════
     GALLERY
════════════════════════════════════════════════════════════════ -->
<section id="gallery" class="gallery-section stars-bg">
  <div class="container">
    <div class="section-header reveal">
      <span class="section-label">In Action</span>
      <h2 class="section-title">Photo <span>Gallery</span></h2>
      <div class="divider"></div>
      <p class="section-subtitle">
        A glimpse into our builds, launches, and competition moments.
      </p>
    </div>

    <!-- Featured large image -->
    <div class="gallery-featured reveal">
      <div class="gallery-frame">
        <img
          src={galleryImages[activeGallery].src}
          alt={galleryImages[activeGallery].alt}
        />
      </div>
    </div>

    <!-- Thumbnail grid -->
    <div class="gallery-grid reveal">
      {#each galleryImages as img, i}
        <button
          class="gallery-thumb"
          class:active={activeGallery === i}
          on:click={() => (activeGallery = i)}
          aria-label="View Image {i + 1}"
          id="gallery-thumb-{i}"
        >
          <img src={img.src} alt={img.alt} loading="lazy" />
        </button>
      {/each}
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════════
     VIDEOS
════════════════════════════════════════════════════════════════ -->
<section id="videos" class="videos-section">
  <div class="container">
    <div class="section-header reveal">
      <span class="section-label">Watch Us Fly</span>
      <h2 class="section-title">Launch <span>Videos</span></h2>
      <div class="divider"></div>
      <p class="section-subtitle">
        From workshop build sessions to competition launches — watch Matador
        Rocketry in action.
      </p>
    </div>

    <div class="videos-grid">
      {#each videos as vid, i}
        <article
          class="video-card glass-card reveal"
          style="--delay:{i * 0.1}s"
          id="video-{vid.id}"
        >
          <div class="video-wrap">
            <video
              src={vid.src}
              controls
              preload="metadata"
              playsinline
              aria-label="Video {i + 1}"
              class="video-player"
            >
              Your browser does not support HTML5 video.
            </video>
          </div>
        </article>
      {/each}
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════════
     CONTACT
════════════════════════════════════════════════════════════════ -->
<section id="contact" class="contact-section stars-bg">
  <div class="container contact-grid">
    <!-- Info Side -->
    <div class="contact-info reveal">
      <span class="section-label">Get In Touch</span>
      <h2 class="section-title">Join the <span>Mission</span></h2>
      <div class="divider"></div>
      <p class="section-subtitle" style="max-width:100%">
        Interested in joining Matador Rocketry, partnering as a sponsor, or just
        have a question? We'd love to hear from you!
      </p>

      <div class="contact-cards">
        <a
          href="mailto:matadorrocketry@mvhs.edu"
          class="contact-item glass-card"
          id="contact-email-card"
        >
          <div class="contact-icon" aria-hidden="true">
            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              xmlns="http://www.w3.org/2000/svg"
              aria-hidden="true"
            >
              <rect x="2" y="4" width="20" height="16" rx="2" />
              <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7" />
            </svg>
          </div>
          <div>
            <strong>Email</strong>
            <p>matadorrocketry@mvhs.edu</p>
          </div>
        </a>

        <div class="contact-item glass-card" id="contact-school-card">
          <div class="contact-icon" aria-hidden="true">
            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              xmlns="http://www.w3.org/2000/svg"
              aria-hidden="true"
            >
              <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z" />
              <polyline points="9 22 9 12 15 12 15 22" />
            </svg>
          </div>
          <div>
            <strong>School</strong>
            <p>Monta Vista High School, Cupertino CA</p>
          </div>
        </div>

        <a
          href="https://www.rocketrychallenge.org"
          target="_blank"
          rel="noopener noreferrer"
          class="contact-item glass-card"
          id="contact-arc-card"
        >
          <div class="contact-icon" aria-hidden="true">
            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              xmlns="http://www.w3.org/2000/svg"
              aria-hidden="true"
            >
              <path d="M12 2L2 7l10 5 10-5-10-5z" />
              <path d="M2 17l10 5 10-5M2 12l10 5 10-5" />
            </svg>
          </div>
          <div>
            <strong>Competition</strong>
            <p>American Rocketry Challenge (ARC)</p>
          </div>
        </a>
      </div>
    </div>

    <!-- Form Side -->
    <div class="contact-form-wrap reveal">
      <form
        class="contact-form glass-card"
        on:submit={handleSubmit}
        id="contact-form"
        aria-label="Contact form"
      >
        <h3 class="form-title">Send Us a Message</h3>

        {#if formStatus === "success"}
          <div class="form-alert success" role="alert">
            ✅ Opening your email client... Thanks for reaching out!
          </div>
        {/if}
        {#if formStatus === "error"}
          <div class="form-alert error" role="alert">
            ⚠️ Please fill in all fields before sending.
          </div>
        {/if}

        <div class="form-group">
          <label for="contact-name">Your Name</label>
          <input
            id="contact-name"
            type="text"
            bind:value={formName}
            placeholder="e.g. Jane Doe"
            required
            autocomplete="name"
          />
        </div>

        <div class="form-group">
          <label for="contact-email">Your Email</label>
          <input
            id="contact-email"
            type="email"
            bind:value={formEmail}
            placeholder="you@example.com"
            required
            autocomplete="email"
          />
        </div>

        <div class="form-group">
          <label for="contact-message">Message</label>
          <textarea
            id="contact-message"
            rows="5"
            bind:value={formMessage}
            placeholder="Tell us why you'd like to join, or ask us anything!"
            required
          ></textarea>
        </div>

        <button
          type="submit"
          class="btn btn-primary submit-btn"
          id="contact-submit-btn"
        >
          <svg
            width="18"
            height="18"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2.5"
            aria-hidden="true"
          >
            <line x1="22" y1="2" x2="11" y2="13" />
            <polygon points="22 2 15 22 11 13 2 9 22 2" />
          </svg>
          Send Message
        </button>
      </form>
    </div>
  </div>
</section>

<style>
  /* ── Reveal animation ─────────────────────────────────────────── */
  .reveal {
    opacity: 0;
    transform: translateY(28px);
    transition:
      opacity 0.65s ease var(--delay, 0s),
      transform 0.65s cubic-bezier(0.2, 0.8, 0.2, 1) var(--delay, 0s);
  }
  :global(.reveal.visible) {
    opacity: 1;
    transform: none;
  }

  /* ─── HERO ────────────────────────────────────────────────────── */
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    background: var(--grad-hero);
    padding: 0 2rem;
    text-align: center;
    overflow: hidden;
  }

  .hero-bg-img {
    position: absolute;
    inset: 0;
    background: url("/dark-purple-placeholder.svg") center center / cover
      no-repeat;
    opacity: 0.22;
    z-index: 0;
  }

  .hero-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(
      to bottom,
      rgba(10, 3, 20, 0.2) 0%,
      rgba(10, 3, 20, 0) 40%,
      rgba(10, 3, 20, 0.85) 100%
    );
    z-index: 1;
  }

  .orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    pointer-events: none;
    z-index: 0;
  }
  .orb-1 {
    width: 500px;
    height: 500px;
    top: -100px;
    left: -100px;
    background: radial-gradient(
      circle,
      rgba(107, 53, 196, 0.35) 0%,
      transparent 70%
    );
    animation: float 8s ease-in-out infinite;
  }
  .orb-2 {
    width: 400px;
    height: 400px;
    bottom: -100px;
    right: -80px;
    background: radial-gradient(
      circle,
      rgba(240, 192, 64, 0.2) 0%,
      transparent 70%
    );
    animation: float 10s ease-in-out infinite reverse;
  }
  .orb-3 {
    width: 300px;
    height: 300px;
    top: 40%;
    left: 60%;
    background: radial-gradient(
      circle,
      rgba(155, 103, 232, 0.2) 0%,
      transparent 70%
    );
    animation: float 12s ease-in-out infinite 2s;
  }

  .hero-content {
    position: relative;
    z-index: 2;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.25rem;
    padding-top: 5rem;
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.45rem 1.1rem;
    border-radius: 99px;
    border: 1px solid rgba(240, 192, 64, 0.4);
    background: rgba(240, 192, 64, 0.1);
    font-family: "Outfit", sans-serif;
    font-size: 0.82rem;
    font-weight: 600;
    letter-spacing: 0.05em;
    color: var(--yellow-gold);
    backdrop-filter: blur(8px);
    animation: fade-up 0.8s ease 0.2s both;
  }
  .badge-dot {
    width: 7px;
    height: 7px;
    border-radius: 50%;
    background: var(--yellow-gold);
    box-shadow: 0 0 8px rgba(240, 192, 64, 0.8);
    animation: pulse-glow 2s ease infinite;
  }

  .hero-title {
    font-family: "Outfit", sans-serif;
    line-height: 1;
    animation: fade-up 0.8s ease 0.35s both;
  }
  .hero-line-1 {
    display: block;
    font-size: clamp(3rem, 10vw, 7.5rem);
    font-weight: 900;
    color: #fff;
    letter-spacing: -0.02em;
  }
  .hero-line-2 {
    display: block;
    font-size: clamp(2rem, 7vw, 5rem);
    font-weight: 700;
    background: linear-gradient(90deg, #f0c040, #ffd700, #f5a623, #f0c040);
    background-size: 200% auto;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation:
      fade-up 0.8s ease 0.5s both,
      shimmer 4s linear infinite 1s;
    letter-spacing: 0.05em;
  }

  .hero-subtitle {
    font-size: clamp(0.95rem, 2.5vw, 1.15rem);
    color: rgba(196, 160, 245, 0.85);
    max-width: 580px;
    animation: fade-up 0.8s ease 0.65s both;
    line-height: 1.7;
  }

  .hero-btns {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
    justify-content: center;
    animation: fade-up 0.8s ease 0.8s both;
  }

  .hero-stats {
    display: flex;
    align-items: center;
    gap: 2rem;
    margin-top: 1rem;
    animation: fade-up 0.8s ease 1s both;
  }
  .stat-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.2rem;
  }
  .stat-num {
    font-family: "Outfit", sans-serif;
    font-size: clamp(1.4rem, 3vw, 2rem);
    font-weight: 800;
    color: var(--yellow-gold);
  }
  .stat-label {
    font-size: 0.78rem;
    color: rgba(196, 160, 245, 0.7);
    text-transform: uppercase;
    letter-spacing: 0.1em;
    font-weight: 500;
  }
  .stat-divider {
    width: 1px;
    height: 40px;
    background: rgba(155, 103, 232, 0.3);
  }

  .hero-scroll-hint {
    position: absolute;
    bottom: 2rem;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.4rem;
    color: rgba(255, 255, 255, 0.35);
    font-size: 0.7rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    animation: fade-up 1s ease 1.4s both;
    z-index: 2;
  }
  .scroll-line {
    width: 1px;
    height: 40px;
    background: linear-gradient(
      to bottom,
      rgba(155, 103, 232, 0.7),
      transparent
    );
    animation: float 2s ease-in-out infinite;
  }

  /* ─── ABOUT ───────────────────────────────────────────────────── */
  .about-section {
    background: linear-gradient(180deg, var(--dark) 0%, var(--dark-mid) 100%);
  }

  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: center;
  }

  .about-img-wrapper {
    position: relative;
    border-radius: var(--radius-lg);
    overflow: hidden;
    box-shadow:
      0 20px 60px rgba(0, 0, 0, 0.5),
      0 0 0 1px rgba(107, 53, 196, 0.3);
  }
  .about-img-wrapper img {
    width: 100%;
    height: 480px;
    object-fit: cover;
    display: block;
    transition: transform 0.6s ease;
  }
  .about-img-wrapper:hover img {
    transform: scale(1.03);
  }

  .about-img-badge {
    position: absolute;
    bottom: 1.5rem;
    left: 1.5rem;
    padding: 0.75rem 1rem;
    display: flex;
    align-items: center;
    gap: 0.75rem;
    border-radius: var(--radius-md);
  }
  .about-img-badge strong {
    display: block;
    font-family: "Outfit", sans-serif;
    font-size: 0.95rem;
    font-weight: 700;
    color: #fff;
  }
  .about-img-badge p {
    font-size: 0.78rem;
    color: var(--yellow-gold);
    margin: 0;
  }
  .badge-emoji {
    font-size: 1.8rem;
  }

  .about-body-text {
    color: rgba(196, 160, 245, 0.7);
    font-size: 0.95rem;
    line-height: 1.75;
    margin: 1rem 0;
  }

  .about-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-top: 1rem;
  }
  .tag {
    padding: 0.35rem 0.9rem;
    border-radius: var(--radius-full);
    font-family: "Outfit", sans-serif;
    font-size: 0.78rem;
    font-weight: 600;
    background: rgba(107, 53, 196, 0.2);
    border: 1px solid rgba(155, 103, 232, 0.3);
    color: var(--purple-pale);
    transition: all 0.2s ease;
  }
  .tag:hover {
    background: rgba(107, 53, 196, 0.4);
    border-color: rgba(155, 103, 232, 0.6);
    color: #fff;
  }

  /* ─── ACHIEVEMENTS ────────────────────────────────────────────── */
  .achievements-section {
    background: var(--dark-mid);
  }

  .section-header {
    text-align: center;
    margin-bottom: 3.5rem;
  }
  .section-header .section-subtitle {
    margin: 0 auto;
  }

  .achievements-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }

  .achievement-card {
    padding: 1.75rem;
    transition-delay: var(--delay, 0s);
  }

  .ach-top {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 1rem;
  }
  .ach-icon {
    font-size: 2rem;
  }
  .ach-year {
    font-family: "Outfit", sans-serif;
    font-size: 0.8rem;
    font-weight: 700;
    letter-spacing: 0.12em;
    color: var(--yellow-gold);
    background: rgba(240, 192, 64, 0.1);
    padding: 0.25rem 0.7rem;
    border-radius: var(--radius-full);
    border: 1px solid rgba(240, 192, 64, 0.25);
  }
  .ach-title {
    font-family: "Outfit", sans-serif;
    font-size: 1.05rem;
    font-weight: 700;
    color: #fff;
    margin-bottom: 0.6rem;
    line-height: 1.3;
  }
  .ach-desc {
    font-size: 0.88rem;
    color: rgba(196, 160, 245, 0.7);
    line-height: 1.65;
  }

  /* ─── TEAM ────────────────────────────────────────────────────── */
  .team-section {
    background: var(--dark);
  }

  .team-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1.5rem;
  }

  .member-card {
    overflow: hidden;
    padding: 0;
    transition-delay: var(--delay, 0s);
  }

  .member-img-wrap {
    position: relative;
    height: 200px;
    overflow: hidden;
  }
  .member-img-wrap img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center top;
    transition: transform 0.5s ease;
  }
  .member-card:hover .member-img-wrap img {
    transform: scale(1.06);
  }
  .member-img-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(
      to bottom,
      transparent 50%,
      rgba(10, 3, 20, 0.85) 100%
    );
  }

  .member-info {
    padding: 1.25rem;
  }
  .member-grade {
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--yellow-gold);
    margin-bottom: 0.3rem;
  }
  .member-name {
    font-family: "Outfit", sans-serif;
    font-size: 1.05rem;
    font-weight: 700;
    color: #fff;
    margin-bottom: 0.2rem;
  }
  .member-title {
    font-family: "Outfit", sans-serif;
    font-size: 0.82rem;
    font-weight: 600;
    color: var(--purple-light);
    margin-bottom: 0.1rem;
  }
  .member-role {
    font-size: 0.78rem;
    color: rgba(196, 160, 245, 0.6);
    margin-bottom: 0.75rem;
  }
  .member-bio {
    font-size: 0.82rem;
    color: rgba(196, 160, 245, 0.65);
    line-height: 1.6;
  }

  /* ─── GALLERY ─────────────────────────────────────────────────── */
  .gallery-section {
    background: var(--dark-mid);
  }

  .gallery-featured {
    margin-bottom: 1.25rem;
  }

  .gallery-frame {
    border-radius: var(--radius-lg);
    overflow: hidden;
    position: relative;
    box-shadow: var(--shadow-card);
    background: var(--dark-card);
  }
  .gallery-frame img {
    width: 100%;
    height: 500px;
    object-fit: cover;
    display: block;
    transition: transform 0.5s ease;
  }
  .gallery-frame:hover img {
    transform: scale(1.02);
  }
  .gallery-caption {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 1.5rem;
    background: linear-gradient(to top, rgba(10, 3, 20, 0.9), transparent);
    font-family: "Outfit", sans-serif;
    font-size: 1.1rem;
    font-weight: 600;
    color: #fff;
  }

  .gallery-grid {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    gap: 0.75rem;
  }

  .gallery-thumb {
    position: relative;
    border-radius: var(--radius-md);
    overflow: hidden;
    cursor: pointer;
    border: 2px solid transparent;
    transition: all 0.25s ease;
    padding: 0;
    background: none;
    aspect-ratio: 4/3;
  }
  .gallery-thumb img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    transition: transform 0.4s ease;
  }
  .gallery-thumb:hover img {
    transform: scale(1.08);
  }
  .gallery-thumb.active {
    border-color: var(--yellow-gold);
    box-shadow: 0 0 16px rgba(240, 192, 64, 0.4);
  }
  .gallery-thumb.active img {
    transform: scale(1.04);
  }

  .thumb-overlay {
    position: absolute;
    inset: 0;
    background: rgba(10, 3, 20, 0.45);
    display: flex;
    align-items: flex-end;
    padding: 0.4rem 0.5rem;
    transition: background 0.2s ease;
    opacity: 0;
  }
  .gallery-thumb:hover .thumb-overlay,
  .gallery-thumb.active .thumb-overlay {
    opacity: 1;
    background: rgba(10, 3, 20, 0.55);
  }
  .thumb-overlay span {
    font-family: "Outfit", sans-serif;
    font-size: 0.65rem;
    font-weight: 600;
    color: #fff;
    line-height: 1.2;
  }

  /* ─── VIDEOS ──────────────────────────────────────────────────── */
  .videos-section {
    background: var(--dark);
  }

  .videos-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }

  .video-card {
    overflow: hidden;
    padding: 0;
    transition-delay: var(--delay, 0s);
  }

  .video-wrap {
    position: relative;
    width: 100%;
    aspect-ratio: 16/9;
    background: #000;
    overflow: hidden;
  }

  .video-player {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    border: none;
    outline: none;
  }

  .video-info {
    padding: 1.25rem;
  }
  .video-title {
    font-family: "Outfit", sans-serif;
    font-size: 1rem;
    font-weight: 700;
    color: #fff;
    margin-bottom: 0.5rem;
    line-height: 1.3;
  }
  .video-desc {
    font-size: 0.85rem;
    color: rgba(196, 160, 245, 0.65);
    line-height: 1.6;
    margin-bottom: 0;
  }

  /* ─── CONTACT ─────────────────────────────────────────────────── */
  .contact-section {
    background: var(--dark-mid);
  }

  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1.1fr;
    gap: 4rem;
    align-items: start;
  }

  .contact-cards {
    display: flex;
    flex-direction: column;
    gap: 0.85rem;
    margin-top: 2rem;
  }

  .contact-item {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1rem 1.25rem;
    text-decoration: none;
    color: inherit;
  }
  .contact-item strong {
    display: block;
    font-family: "Outfit", sans-serif;
    font-size: 0.9rem;
    font-weight: 700;
    color: #fff;
  }
  .contact-item p {
    font-size: 0.82rem;
    color: rgba(196, 160, 245, 0.7);
    margin: 0;
  }

  .contact-icon {
    width: 40px;
    height: 40px;
    flex-shrink: 0;
    background: rgba(107, 53, 196, 0.25);
    border-radius: var(--radius-sm);
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--purple-light);
  }
  .contact-icon svg {
    width: 18px;
    height: 18px;
  }
  a.contact-item:hover .contact-icon {
    background: rgba(240, 192, 64, 0.15);
    color: var(--yellow-gold);
  }

  /* Form */
  .contact-form {
    padding: 2.25rem;
  }
  .form-title {
    font-family: "Outfit", sans-serif;
    font-size: 1.4rem;
    font-weight: 700;
    color: #fff;
    margin-bottom: 1.5rem;
  }

  .form-alert {
    padding: 0.75rem 1rem;
    border-radius: var(--radius-sm);
    font-size: 0.88rem;
    margin-bottom: 1rem;
  }
  .form-alert.success {
    background: rgba(52, 211, 153, 0.1);
    border: 1px solid rgba(52, 211, 153, 0.3);
    color: #6ee7b7;
  }
  .form-alert.error {
    background: rgba(248, 113, 113, 0.1);
    border: 1px solid rgba(248, 113, 113, 0.3);
    color: #fca5a5;
  }

  .form-group {
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
    margin-bottom: 1.1rem;
  }
  .form-group label {
    font-family: "Outfit", sans-serif;
    font-size: 0.82rem;
    font-weight: 600;
    color: rgba(196, 160, 245, 0.8);
    letter-spacing: 0.05em;
    text-transform: uppercase;
  }
  .form-group input,
  .form-group textarea {
    background: rgba(45, 10, 92, 0.3);
    border: 1px solid rgba(107, 53, 196, 0.35);
    border-radius: var(--radius-sm);
    padding: 0.8rem 1rem;
    font-family: "Space Grotesk", sans-serif;
    font-size: 0.92rem;
    color: #fff;
    outline: none;
    transition:
      border-color 0.2s ease,
      background 0.2s ease;
    resize: vertical;
  }
  .form-group input::placeholder,
  .form-group textarea::placeholder {
    color: rgba(155, 103, 232, 0.45);
  }
  .form-group input:focus,
  .form-group textarea:focus {
    border-color: var(--purple-light);
    background: rgba(74, 26, 140, 0.25);
  }

  .submit-btn {
    width: 100%;
    justify-content: center;
    margin-top: 0.5rem;
  }

  /* ─── Responsive ──────────────────────────────────────────────── */
  @media (max-width: 1100px) {
    .team-grid {
      grid-template-columns: repeat(2, 1fr);
    }
    .achievements-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (max-width: 900px) {
    .about-grid {
      grid-template-columns: 1fr;
    }
    .about-img-col {
      order: -1;
    }
    .gallery-grid {
      grid-template-columns: repeat(4, 1fr);
    }
    .gallery-frame img {
      height: 360px;
    }
    .videos-grid {
      grid-template-columns: 1fr 1fr;
    }
    .video-wrap {
      aspect-ratio: 16/9;
    }
    .contact-grid {
      grid-template-columns: 1fr;
      gap: 2rem;
    }
  }

  @media (max-width: 600px) {
    .hero-stats {
      gap: 1rem;
    }
    .team-grid {
      grid-template-columns: 1fr 1fr;
    }
    .achievements-grid {
      grid-template-columns: 1fr;
    }
    .videos-grid {
      grid-template-columns: 1fr;
    }
    .gallery-grid {
      grid-template-columns: repeat(3, 1fr);
    }
    .gallery-frame img {
      height: 280px;
    }
  }

  @media (max-width: 400px) {
    .team-grid {
      grid-template-columns: 1fr;
    }
    .gallery-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }
</style>
