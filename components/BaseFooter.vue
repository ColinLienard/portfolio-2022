<script setup lang="ts">
const scrollTo = useScrollTo();
const route = useRoute();

const handleScrollTo = (target: string) => {
  // If the current page is the home
  if (Object.keys(route.params).length === 0) {
    scrollTo(target);
    return;
  }

  navigateTo(`/${target}`);
};
</script>

<template>
  <NuxtLayout name="section">
    <footer class="footer">
      <SpotifyListening />
      <div class="links-list">
        <ul class="list">
          <li>
            <button class="button" @click="handleScrollTo('#portfolio')">
              Portfolio
            </button>
          </li>
          <li>
            <button class="button" @click="handleScrollTo('#about')">
              À propos
            </button>
          </li>
          <li>
            <button class="button" @click="handleScrollTo('#contact')">
              Contact
            </button>
          </li>
        </ul>
        <ul class="list">
          <li>
            <a
              class="button"
              href="https://github.com/ColinLienard"
              target="_blank"
            >
              GitHub
            </a>
          </li>
          <li>
            <a
              class="button"
              href="https://www.linkedin.com/in/colin-lienard-83490a1a4/"
              target="_blank"
            >
              LinkedIn
            </a>
          </li>
          <li>
            <a class="button" href="mailto:contact@colin-lienard.fr">
              contact@colin-lienard.fr
            </a>
          </li>
        </ul>
        <ul class="list">
          <li>
            <button class="button">Mentions légales</button>
          </li>
        </ul>
      </div>
      <p class="copyright">
        © Copyright 2022 - Tous droits réservés, Colin Lienard
      </p>
    </footer>
  </NuxtLayout>
</template>

<style scoped lang="scss">
@use '../styles/screens';
@use '../styles/typography';
@use '../styles/variables';

.footer {
  display: flex;
  flex-direction: column;
  gap: 3rem;
  padding-bottom: 2rem;

  @include screens.laptop {
    gap: 6rem;
    padding-bottom: 4rem;
  }

  .title {
    @include typography.heading-3;

    text-align: center;
  }

  .links-list {
    display: flex;
    flex-direction: column;
    gap: 2rem;

    @include screens.laptop {
      display: grid;
      grid-template-columns: repeat(3, 16rem);
    }

    .list {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 1rem;

      .button {
        text-align: center;
        color: variables.$grey;
        transition: color 0.3s ease-in-out;

        &:hover {
          color: variables.$white;
        }
      }
    }
  }

  .copyright {
    color: variables.$grey;
    text-align: center;
  }
}
</style>
