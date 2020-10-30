<template>
  <main>

    <nav>
      <ul>
        <li v-for="route in routes">
          <router-link :to="route.path">{{ route.title }}</router-link>
        </li>
      </ul>
    </nav>

    <router-view />
    
  </main>
</template>
<script>
  import { routes } from './routes';

  export default {
    data() {
      return {
        routes
      }
    }
  }
</script>
<style lang="scss">
main {
  width: 100%;
  height: 100vh;
}
</style>
