<template>
  <form @submit.prevent="enviarAvaliacao">
  <label for="cafe">Escolha um café</label>
  <select id="cafe" v-model="cafeSelecionado" required>
    <option disabled value="">Selecione um café</option>
    <option v-for="cafe in cafes" :key="cafe.id" :value="cafe.id">
      {{ cafe.nome }}
    </option>
  </select>

  <label for="nota">Nota</label>
  <input
    id="nota"
    v-model="nota"
    type="number"
    min="0"
    max="10"
    step="0.1"
    required
  >

  <button type="submit">Enviar avaliação</button>
</form>

<p v-if="mensagem" class="mensagem" role="status">{{ mensagem }}</p>

</template>
<script setup>

import { ref } from 'vue'
import cafes from '@/data/cafes'

const cafeSelecionado = ref('')
const nota = ref('')
const mensagem = ref('')

function enviarAvaliacao() {
  if (
    cafeSelecionado.value === '' ||
    nota.value === '' ||
    Number(nota.value) < 0 ||
    Number(nota.value) > 10
  ) {
    mensagem.value = 'Selecione um café e informe uma nota entre 0 e 10.'
    return
  }

  const cafe = cafes.value.find((item) => {
    return String(item.id) === String(cafeSelecionado.value)
  })

  if (!cafe) {
    mensagem.value = 'Café não encontrado.'
    return
  }

  cafe.nota = Number(nota.value)

  mensagem.value = 'Avaliação enviada com sucesso!'

  cafeSelecionado.value = ''
  nota.value = ''
}



</script>
<style scoped>
.mensagem {
  max-width: 580px;
  margin: 18px auto 0;
  padding: 14px 18px;
  border: 1px solid #d9c2a9;
  border-radius: 12px;
  background: #fff8e8;
  color: #5f402c;
  font-weight: 600;
  text-align: center;
}

form {
  max-width: 580px;
  margin: 28px auto;
  padding: clamp(28px, 6vw, 46px);
  border: 1px solid #eadcc5;
  border-radius: 24px;
  background:
    radial-gradient(circle at 100% 0, rgba(209, 179, 153, 0.32), transparent 31%),
    linear-gradient(135deg, #fffdf7, #fff4df);
  box-shadow: 0 18px 42px rgba(77, 47, 28, 0.14);
}

form::before {
  display: block;
  margin-bottom: 30px;
  color: #3d2517;
  content: 'Avalie um café';
  font-family: Georgia, 'Times New Roman', serif;
  font-size: clamp(2rem, 5vw, 2.8rem);
  font-weight: 700;
  text-align: center;
}

label {
  display: block;
  margin: 18px 0 7px;
  color: #5f402c;
  font-size: 0.95rem;
  font-weight: 700;
}

input,
select {
  width: 100%;
  padding: 14px 15px;
  border: 1px solid #d9c2a9;
  border-radius: 10px;
  outline: none;
  background: rgba(255, 255, 255, 0.88);
  color: #3d2517;
  font: inherit;
  transition: border-color 0.2s ease, box-shadow 0.2s ease;
}

input::placeholder {
  color: #a88b76;
}

input:focus,
select:focus {
  border-color: #8a6247;
  box-shadow: 0 0 0 4px rgba(209, 179, 153, 0.42);
}

button {
  width: 100%;
  margin-top: 30px;
  padding: 15px 20px;
  border: 0;
  border-radius: 12px;
  background: #6f4e37;
  color: #fffdf7;
  cursor: pointer;
  font: inherit;
  font-weight: 700;
  letter-spacing: 0.02em;
  box-shadow: 0 9px 18px rgba(77, 47, 28, 0.22);
  transition: background 0.2s ease, transform 0.2s ease, box-shadow 0.2s ease;
}

button:hover {
  background: #513522;
  box-shadow: 0 13px 22px rgba(77, 47, 28, 0.28);
  transform: translateY(-3px);
}

button:focus-visible {
  outline: 3px solid #d1b399;
  outline-offset: 3px;
}

@media (max-width: 600px) {
  form {
    margin: 12px auto;
    padding: 30px 22px;
    border-radius: 18px;
  }
}

</style>
