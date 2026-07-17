<template>
  <form @submit.prevent="adicionarCafe">
    <label for="nome">Nome do café</label>
    <input id="nome" v-model="nome" type="text" required>

    <label for="local">Fazenda ou local</label>
    <input id="local" v-model="local" type="text" required>

    <button type="submit">Adicionar à competição</button>
  </form>

  <p v-if="mensagem" class="mensagem" role="status">{{ mensagem }}</p>
</template>

<script setup>
import { ref } from 'vue'
import cafes from '@/data/cafes'

const nome = ref('')
const local = ref('')
const mensagem = ref('')

function normalizarNome(valor) {
  return valor
    .normalize('NFD')
    .replace(/[\u0300-\u036f]/g, '')
    .trim()
    .toLocaleLowerCase('pt-BR')
}

function adicionarCafe() {
  const nomeLimpo = nome.value.trim()
  const localLimpo = local.value.trim()

  if (!nomeLimpo || !localLimpo) {
    mensagem.value = 'Preencha o nome e o local do café.'
    return
  }

  const cafeJaExiste = cafes.value.some((cafe) => {
    return normalizarNome(cafe.nome) === normalizarNome(nomeLimpo)
  })

  if (cafeJaExiste) {
    mensagem.value = 'Esse café já está na competição.'
    return
  }

  cafes.value.push({
    id: Date.now(),
    nome: nomeLimpo,
    local: localLimpo,
    nota: 0,
  })

  mensagem.value = 'Café adicionado à competição!'
  nome.value = ''
  local.value = ''
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
  content: 'Entrar na competição';
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

input {
  width: 100%;
  padding: 14px 15px;
  border: 1px solid #d9c2a9;
  border-radius: 10px;
  outline: none;
  background: rgba(255, 255, 255, 0.88);
  color: #3d2517;
  font: inherit;
}

input:focus {
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
}

button:hover {
  background: #513522;
}

button:focus-visible {
  outline: 3px solid #d1b399;
  outline-offset: 3px;
}
</style>
