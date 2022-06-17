<template>
  <main>
    <section class="section-hero section">
      <div class="container grid grid-two-column">
        <div class="section-hero-data">
          <p class="hero-top-data">Tempat Terbaikmu</p>
          <h1 class="hero-heading">MY RESTAURANT</h1>
          <p class="hero-paragraph">
            Pesan Makanananmu dengan aman, mudah, nyaman, dan tentunya cepat dan
            enak
          </p>
          <div>
            <a to="#" class="hero-btn">Pesan Sekarang</a>
          </div>
        </div>
        <div class="section-hero-image">
          <img src="../assets/images/hero.jpg" alt="" class="hero-img" />
        </div>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  name: "HeroComponent",
};
</script>

<style lang="scss" scoped>
.section {
  padding: 40px 0;
}

.container {
  max-width: 90%;
  margin: 0 auto;
}

.grid {
  display: grid;
  gap: 10px;
}

.grid-two-column {
  grid-template-columns: repeat(2, 1fr);
}

.section-hero {
  background-color: #eaf3fa;
}

.section-hero-data {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: auto;

  .hero-top-data {
    text-transform: uppercase;
    font-weight: 500;
    font-size: 12px;
    margin-top: 15px;
    color: rgb(119 164 229);
  }

  .hero-heading {
    text-transform: uppercase;
    font-weight: 700;
    font-size: 48px;
    margin-top: 2px;
  }

  .hero-paragraph {
    margin-top: 10px;
    margin-bottom: 50px;
    max-width: 23rem;
    font-size: 16px;
  }
}

.section-hero-image {
  display: flex;
  justify-content: center;
  align-items: center;

  .hero-img {
    max-width: 90%;
  }
}

.hero-btn {
  background: -webkit-linear-gradient(
    0deg,
    rgb(160 193 244) 0%,
    rgb(119 164 229) 100%
  );
  padding: 15px 20px;
  border: none;
  color: #ffffff;
  border-radius: 5px;
  display: inline-block;
  text-transform: uppercase;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  margin-bottom: 15px;

  &:hover,
  :active {
    box-shadow: 0 20px 20px 0 rgb(132 144 255 / 30%);
  }
}

@media (max-width: 980px) {
  .container {
    padding: 0 3.2rem;
  }

  .section-hero {
    h1 {
      line-height: 1.05;
    }
  }
}

@media only screen and (max-width: 780px) {
  .container {
    max-width: 720px;
  }

  .section-hero {
    .grid-two-column {
      grid-template-columns: 1fr;
    }
  }

  .grid-two-column > .section-hero-data {
    order: 2;
  }

  .grid-two-column > .section-hero-image {
    order: 1;
  }

  .section-hero-data {
    align-items: center;
  }

  .hero-heading {
    text-align: center;
  }
  .hero-paragraph {
    text-align: center;
    margin-top: 2rem;
    font-size: 16px;
  }

  .section-hero {
    img {
      width: 100%;
    }
  }
}
</style>