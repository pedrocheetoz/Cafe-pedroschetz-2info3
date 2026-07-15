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
  *{
    color: black;
  }

  .button{
    text-decoration: none;
    border-radius: 10px;
    padding: 15px;
    background-color: #D1B399;
    transition: all 0.3s;
  }
  .bot-text{
    color: #6F4E37;

  }
  .button:hover{
    border-color: white;
    color: black;
    transform: translateY(2px);
  }

</style>
