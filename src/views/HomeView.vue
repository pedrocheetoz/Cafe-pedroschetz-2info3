<template>
  <main>
    <div class="hero">
      <div class="hero-texto">
        <h1>
          Campeonato de café
        </h1>
        <p>
          Torneio de alguma coisa de café
        </p>
   </div>
      <img src="@/assets/img/cafe.png" alt="">

    </div>
  </main>
      <button class="button">
        <RouterLink to="/ranking" class="bot-text">Ver Ranking</RouterLink>
      </button>

</template>
  <script>

</script>
<style>
  .hero {
    position: relative;
    isolation: isolate;
    display: grid;
    grid-template-columns: 1.25fr 0.75fr;
    align-items: center;
    gap: 40px;
    max-width: 1100px;
    min-height: 440px;
    margin: 20px auto 0;
    padding: 64px clamp(28px, 7vw, 80px);
    overflow: hidden;
    border: 1px solid #eadcc5;
    border-radius: 28px;
    background:
      radial-gradient(circle at 87% 22%, #f0d9b8 0, transparent 22%),
      linear-gradient(135deg, #fffdf7 0%, #fff4df 100%);
    box-shadow: 0 18px 45px rgba(77, 47, 28, 0.14);
  }

  .hero::before,
  .hero::after {
    position: absolute;
    z-index: -1;
    border-radius: 50%;
    content: '';
  }

  .hero::before {
    right: -115px;
    bottom: -145px;
    width: 360px;
    height: 360px;
    border: 48px solid rgba(209, 179, 153, 0.24);
  }

  .hero::after {
    top: 40px;
    left: -45px;
    width: 105px;
    height: 105px;
    background: rgba(209, 179, 153, 0.22);
  }

  .hero-texto {
    max-width: 580px;
  }

  .hero-texto::before {
    display: block;
    margin-bottom: 16px;
    color: #8a6247;
    content: '☕  SABOR, PAIXÃO E QUALIDADE';
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.14em;
  }

  .hero-texto h1 {
    margin: 0;
    color: #3d2517;
    font-family: Georgia, 'Times New Roman', serif;
    font-size: clamp(2.6rem, 6vw, 4.8rem);
    line-height: 1.04;
  }

  .hero-texto p {
    max-width: 440px;
    margin: 22px 0 0;
    color: #765d4c;
    font-size: clamp(1rem, 2vw, 1.18rem);
    line-height: 1.7;
  }

  .hero img {
    justify-self: center;
    width: min(100%, 280px);
    filter: drop-shadow(0 18px 14px rgba(63, 37, 22, 0.24));
    transform: rotate(-4deg);
    transition: transform 0.25s ease;
  }

  .hero:hover img {
    transform: rotate(2deg) translateY(-8px);
  }

  .button {
    position: relative;
    display: block;
    margin: -28px auto 24px;
    padding: 0;
    overflow: hidden;
    border: 0;
    border-radius: 12px;
    background: #6f4e37;
    box-shadow: 0 10px 20px rgba(77, 47, 28, 0.24);
    cursor: pointer;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }

  .bot-text {
    display: block;
    padding: 15px 26px;
    color: #fffdf7;
    text-decoration: none;
    font-size: 1rem;
    font-weight: 700;
  }

  .button:hover {
    box-shadow: 0 15px 26px rgba(77, 47, 28, 0.3);
    transform: translateY(-4px);
  }

  .button:focus-within {
    outline: 3px solid #d1b399;
    outline-offset: 4px;
  }

  @media (max-width: 700px) {
    .hero {
      grid-template-columns: 1fr;
      gap: 30px;
      min-height: 0;
      padding: 48px 28px 40px;
      text-align: center;
    }

    .hero-texto {
      max-width: none;
    }

    .hero-texto p {
      margin-right: auto;
      margin-left: auto;
    }

    .hero img {
      width: 180px;
      grid-row: 1;
    }

    .hero-texto {
      grid-row: 2;
    }
  }

  @media (prefers-reduced-motion: reduce) {
    .hero img,
    .button {
      transition: none;
    }
  }

</style>
