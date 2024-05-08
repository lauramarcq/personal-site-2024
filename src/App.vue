<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { useMatchMedia } from '@/composables/useScreenSize'
import TheFooter from './components/TheFooter.vue'

const desktopScreen = useMatchMedia('(min-width: 1024px)')
</script>

<template>
  <header>
    <div class="name" v-if="desktopScreen">laura<span>.</span>valdivia</div>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/projects">Projects</RouterLink>
      <RouterLink to="/about">About Me</RouterLink>
    </nav>
  </header>
  <RouterView />
  <the-footer />
</template>
<style scoped>
header {
  line-height: 1.5;
  min-height: 100px;
  background-color: #232133;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    flex-direction: row;
    .name {
      font-size: 1.5rem;
      font-weight: 900;
      margin-left: 5%;
      color: rgba(255, 255, 255, 0.896);
      span {
        color: #ee595d;
        font-size: 3rem;
      }
    }
  }
  nav {
    font-size: 1.3rem;
    display: flex;
    justify-content: flex-end;
    margin-right: 2%;
  }

  nav a {
    padding: 30px;
  }
}
</style>
