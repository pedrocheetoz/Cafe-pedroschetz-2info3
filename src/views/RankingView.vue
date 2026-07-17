<template>
  <div class="ranking-view">
      <!-- <ul>
      <li>
        Café Arabe - Fazenda Água Doce - 9,99
      </li>
      <li>
        Café Java - Fazenda James Gosling - 8,75
      </li>
      <li>
        Café Robusto - Fazenda Luminosa - 10
      </li>
      <li>
        Café Bourbon - Hotel Fazenda  - 7,5
      </li>
      <li>
        Café Geisha - Sitio do Pica-Pau Amarelo  - 9
      </li>
    </ul> -->
    <ul>
      <li v-for="cafe in cafesOrdenados"
      :key="cafe.id"
       :nome="cafe.nome"
       :local="cafe.local"
       :nota="cafe.nota"
       >

       Nome: {{ cafe.nome }}
        Local: {{ cafe.local }}
        Nota: {{ cafe.nota }}
      </li>
    </ul>

  </div>

</template>
<script setup>
import { computed } from 'vue';
import cafes from '@/data/cafes';

  const cafesOrdenados = computed(() => {
    return [...cafes.value].sort((a, b) => b.nota - a.nota)
  }
)

</script>
<style scoped>
.ranking-view {
  --espresso: #3d2517;
  --coffee: #6f4e37;
  --cream: #fff8e8;
  --caramel: #d1b399;
  max-width: 850px;
  margin: 30px auto;
  padding: 42px 36px;
  border: 1px solid #eadcc5;
  border-radius: 24px;
  background: linear-gradient(135deg, #fffdf7 0%, var(--cream) 100%);
  box-shadow: 0 16px 38px rgba(77, 47, 28, 0.14);
}

.ranking-view::before {
  content: 'Ranking dos Cafés';
  display: block;
  margin-bottom: 8px;
  color: var(--espresso);
  font-family: Georgia, 'Times New Roman', serif;
  font-size: clamp(1.8rem, 4vw, 2.5rem);
  font-weight: 700;
  text-align: center;
}

.ranking-view ul::before {
  content: 'Os melhores sabores, organizados pela avaliação';
  display: block;
  margin-bottom: 12px;
  color: #826957;
  font-size: 0.95rem;
  text-align: center;
}

.ranking-view ul {
  display: grid;
  gap: 14px;
  margin: 0;
  padding: 0;
  list-style: none;
}

.ranking-view li {
  position: relative;
  display: grid;
  gap: 4px;
  min-height: 96px;
  padding: 18px 82px 18px 84px;
  border: 1px solid #eadcc5;
  border-radius: 16px;
  background: #fff;
  color: var(--espresso);
  font-size: 1rem;
  font-weight: 600;
  line-height: 1.55;
  box-shadow: 0 5px 12px rgba(77, 47, 28, 0.06);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.ranking-view li:hover {
  transform: translateY(-3px);
  box-shadow: 0 12px 22px rgba(77, 47, 28, 0.14);
}

.ranking-view li::before {
  position: absolute;
  top: 50%;
  left: 20px;
  display: grid;
  width: 44px;
  height: 44px;
  place-items: center;
  border-radius: 50%;
  background: var(--coffee);
  color: #fff;
  content: counter(rank);
  counter-increment: rank;
  font-weight: 700;
  transform: translateY(-50%);
}

.ranking-view ul {
  counter-reset: rank;
}

.ranking-view li::after {
  position: absolute;
  top: 50%;
  right: 22px;
  color: var(--coffee);
  content: '★';
  font-size: 1.45rem;
  transform: translateY(-50%);
}

.ranking-view li:nth-child(1) {
  border-color: #e6bc54;
  background: linear-gradient(90deg, #fff9e8, #fff);
}

.ranking-view li:nth-child(1)::before {
  background: #d69e2e;
}

.ranking-view li:nth-child(2)::before {
  background: #84909b;
}

.ranking-view li:nth-child(3)::before {
  background: #b7793f;
}

@media (max-width: 600px) {
  .ranking-view {
    margin: 10px auto;
    padding: 30px 18px;
    border-radius: 18px;
  }

  .ranking-view li {
    padding: 16px 54px 16px 66px;
    font-size: 0.92rem;
  }

  .ranking-view li::before {
    left: 14px;
    width: 36px;
    height: 36px;
  }

  .ranking-view li::after {
    right: 16px;
    font-size: 1.2rem;
  }
}

</style>
