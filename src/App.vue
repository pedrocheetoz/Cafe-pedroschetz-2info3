<template>
    <header>
      <div>
        <nav>
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/avaliacao">Avaliações</RouterLink>
          <RouterLink to="/ranking">Ranking</RouterLink>
        </nav>
      </div>
    </header>

    <main>

      <RouterView />

    </main>

</template>
<script>
  import { RouterLink, RouterView } from 'vue-router';
</script>

<style>

</style>
