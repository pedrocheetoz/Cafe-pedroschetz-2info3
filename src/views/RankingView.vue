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
      <li v-for="cafe in cafesOrdenados" :key="cafe.id">
        Nome: {{ cafe.nome }}
        Local: {{ cafe.local }}
        Nota: {{ cafe.nota }}
      </li>
    </ul>

  </div>

</template>
<script>
import { computed, ref } from 'vue';

const cafes = [
  {nome: 'Café Arabe',
    local: 'Fazenda Água Doce',
    nota:'9.99',
    id:'1'
  },
  {nome: 'Café Java',
    local: 'Fazenda James Gosling',
    nota:'8.75',
    id:'2'
  },
  {nome: 'Café Robusto',
    local: 'Fazenda Luminosa',
    nota:'10',
    id:'3'
  },
  {nome: 'Café Bourbon',
    local: 'Hotel Fazenda',
    nota:'7.5',
    id:'4'
  },
  {nome: 'Café Geisha', 
    local: 'Sitio do Pica-Pau Amarelo',
    nota:'9',
    id:'5'
  },
]
  const cafesOrdenados = computed(() => {
    return [...cafes.value].sort((a, b) => b.nota - a.nota)
  }
)

</script>
<style>

</style>
