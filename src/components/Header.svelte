<script>
  import { _ } from "../services/i18n";
  import { pages, mobilePages } from "../strings.js";
  export let page;
  export let handleClickNavigation;

  const openStore = (store) => {
    if (store === 'app') {
      window.open('https://apps.apple.com/us/app/lemmi/id1519868911')
    } else {
      window.open('http://play.google.com/store/apps/details?id=com.jenix.lemmi')
    }
  }
</script>

<header>
  <div class="header-wrapper">
    <img class="mobile-hero-image" src="images/appIcon.svg" alt="Lemmi Logo" />
    <img
      class="hero-image"
      src="images/hero-image.png"
      alt="Lemmi shown on an iPad and iPhone"
    />
    <section class="hero-info">
      <h1 class="title">
        <img class="logo" src="images/appIcon.svg" alt="Lemmi Logo" />
        {$_('hero.title')}<sup>®</sup>
      </h1>
      <h3 class="subtitle">{$_('hero.subtitle')}</h3>
      <div class="store-icons">
        <button
          on:click={() => openStore('app')}
        >
          <img
            class="app-icon"
            src="images/app-store.png"
            alt="Download on the App Store" />
        </button>
        <button
          on:click={() => openStore('play')}
        >
          <img
            class="play-icon"
            src="images/play-store.png"
            alt="Download on the Play Store" />
        </button>
      </div>
    </section>
  </div>
</header>
<nav class="nav-bar">
  <ul>
    {#each Object.values(pages) as pageTitle}
      <li>
        <button
          on:click={() => handleClickNavigation(pageTitle)}
          class={`${page === pageTitle ? 'selected' : ''}`}
        >{pageTitle}</button>
      </li>
    {/each}
  </ul>
</nav>
<nav class="mobile-nav">
  <ul>
    {#each Object.values(mobilePages) as pageTitle}
      <li>
        <button
          on:click={() => handleClickNavigation(pageTitle)}
          class={`${page === pageTitle ? 'selected' : ''}`}
        >{pageTitle}</button>
      </li>
    {/each}
  </ul>
</nav>

<style>
  header {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 40px;
  }

  .header-wrapper {
    display: flex;
    justify-content: center;
  }

  .lemmi-description {
    text-align: center;
    margin: 30px auto 0 auto;
    max-width: 800px;
  }

  .hero-image {
    height: 290px;
    width: 290px;
  }

  .hero-info {
    display: flex;
    flex-direction: column;
    margin-left: 50px;
    width: 35%;
    max-width: 345px;
  }

  .mobile-hero-image {
    height: 120px;
    width: 120px;
    display: none;
  }

  .logo {
    height: 40px;
  }

  .title {
    margin-top: 15px;
    font-size: 3rem;
    font-weight: 500;
  }

  .title sup {
    font-size: 1.1rem;
    vertical-align: top;
  }

  .subtitle {
    font-size: 2.25rem;
    margin: 0;
    font-weight: 500;
  }

  .store-icons {
    margin-top: 20px;
    display: flex;
  }

  .store-icons button {
    cursor: pointer;
    width: 150px;
    padding: 0;
    background: none;
    border: none;
  }
  
  .store-icons button:hover img {
    opacity: 0.8;
  }

  .app-icon {
    height: 45px;
    margin: 0 10px 0 0;
  }

  .play-icon {
    height: 47px;
    margin: -1px 5px 0 0;
  }

  .mobile-nav {
    display: none;
  }

  .nav-bar {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 60px;
    background-color: #ffffff;
  }

  .nav-bar ul {
    display: flex;
  }

  .nav-bar button, .mobile-nav button {
    margin: 0;
    background: none;
    border: none;
    font-size: 1.75rem;
    cursor: pointer;
    margin: 0 20px;
  }

  .nav-bar button:hover, .mobile-nav button:hover, .nav-bar button.selected, .mobile-nav button.selected {
    color: #25548c
  }

  @media screen and (max-width: 936px) {
    .hero-info {
      width: 45%;
    }
  }

  @media screen and (max-width: 767px) {
    .header-wrapper {
      flex-direction: column;
      text-align: center;
      align-items: center;
      justify-content: center;
      padding: 40px 15px;
    }

    .hero-info {
      margin-left: 0px;
      width: 100%;
      max-width: 500px;
    }

    .store-icons {
      justify-content: space-around;
    }

    .store-icons button {
      width: 50%;
      display: flex;
      justify-content: center;
    }
  }

  @media screen and (max-width: 674px) {
    .nav-bar {
      display: none;
    }

    .mobile-nav {
      display: flex;
      background-color: #ffffff;
      height: 5rem;
    }

    .mobile-nav ul {
      width: 100%;
      display: flex;
      flex-direction: column;
      flex-wrap: wrap;
      justify-content: space-around;
    }

    .mobile-nav li {
      height: 30px;
      display: flex;
      justify-content: center;
    }

    .mobile-nav button {
      font-size: 1.15rem;
    }
  }

  @media screen and (max-width: 619px) {
    .mobile-hero-image {
      display: flex;
    }

    .hero-image, .logo {
      display: none;
    }

    .app-icon {
      height: 35px;
      margin: 0;
    }

    .play-icon {
      height: 35px;
      margin: 0;
    }

    .lemmi-description {
      margin-top: 5px;
    }
  }
</style>