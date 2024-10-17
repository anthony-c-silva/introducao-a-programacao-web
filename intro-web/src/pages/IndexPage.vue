<template>
  <q-page class="flex flex-center column q-pa-md">
    <!-- Título principal da página -->
    <q-toolbar class="q-mb-md">
      <q-toolbar-title class="text-h4 text-center">Bem-vindo à Minha Página Criativa</q-toolbar-title>
    </q-toolbar>

    <!-- Parágrafos descritivos -->
    <q-paragraph class="text-center q-mb-lg">
      Aqui você encontrará informações sobre alguns dos meus tópicos e interesses favoritos. Espero que você goste e se
      inspire!
    </q-paragraph>

    <q-heading class="text-h5 q-mb-md">
      Experimente nosso separador de números pares e ímpares
    </q-heading>

    <!-- Campo para o usuário digitar os números -->
    <q-paragraph>Digite números separados por vírgula:</q-paragraph>
    <q-input filled v-model="inputNumeros" placeholder="Exemplo: 1, 2, 3, 4, 5" />

    <q-btn class="q-mt-md q-mb-lg" color="primary" @click="processarNumeros">
      Separar Números
    </q-btn>

    <!-- Área para exibir os resultados -->
    <q-heading class="text-h6">Resultado:</q-heading>
    <q-paragraph><strong>Pares:</strong> {{ resultado.pares.join(', ') }}</q-paragraph>
    <q-paragraph><strong>Ímpares:</strong> {{ resultado.impares.join(', ') }}</q-paragraph>

    <!-- Links para outros sites -->
    <q-heading class="text-h6 q-mt-lg">Links Relevantes</q-heading>
    <q-paragraph>Abaixo estão alguns links para sites que eu gosto de visitar:</q-paragraph>
    <q-list bordered>
      <q-item clickable v-ripple tag="a" href="https://www.github.com" target="_blank">
        <q-item-section>GitHub</q-item-section>
      </q-item>
      <q-item clickable v-ripple tag="a" href="https://www.behance.net" target="_blank">
        <q-item-section>Behance</q-item-section>
      </q-item>
      <q-item clickable v-ripple tag="a" href="https://www.psychologytoday.com" target="_blank">
        <q-item-section>Psychology Today</q-item-section>
      </q-item>
    </q-list>

    <!-- Imagem de exemplo -->
    <q-heading class="text-h6 q-mt-lg">Imagem Inspiradora</q-heading>
    <q-paragraph>Esta é uma imagem que me inspira a cada dia:</q-paragraph>
    <q-img src="https://warcontent.com/wp-content/uploads/2020/03/frases-inspiradoras-para-desenvolvedores-3-1024x576.jpg.webp"
      alt="Imagem Inspiradora" width="400px" class="q-mb-md" />

    <!-- Citação com blockquote -->
    <blockquote>
      "A simplicidade é o último grau de sofisticação." – Leonardo da Vinci
    </blockquote>
  </q-page>
</template>

<script setup>
import { ref } from 'vue';

// Definindo um estado reativo para o input e resultado
const inputNumeros = ref('');
const resultado = ref({ pares: [], impares: [] });

// Função para separar números pares e ímpares
function separarParesImpares(numeros) {
  const pares = numeros.filter(numero => numero % 2 === 0);
  const impares = numeros.filter(numero => numero % 2 !== 0);

  return { pares, impares };
}

// Função que processa os números do input e atualiza o resultado
function processarNumeros() {
  const numerosArray = inputNumeros.value
    .split(',')
    .map(num => parseInt(num.trim()))
    .filter(num => !isNaN(num));

  resultado.value = separarParesImpares(numerosArray);
}
</script>

<style scoped>
/* Estilos adicionais para ajustar o layout */
.q-page {
  max-width: 600px;
  margin: auto;
}

blockquote {
  font-style: italic;
  color: #555;
  border-left: 4px solid #ccc;
  padding-left: 10px;
  margin: 20px 0;
}
</style>
