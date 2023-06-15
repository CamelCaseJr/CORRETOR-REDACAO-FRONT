<template>
  <q-drawer
    :model-value="value"
    show-if-above
    :mini="miniState"
    @mouseover="handleMouseOver"
    @mouseout="handleMouseOut"
    :width="200"
    :breakpoint="500"
    bordered
    :class="$q.dark.isActive ? 'bg-#363636' : 'bg-white'"
  >
    <q-scroll-area class="fit" :horizontal-thumb-style="{ opacity: 0 }">
      <q-list class="text-blue-grey-7" padding>
        <q-item clickable v-ripple to="home">
          <q-item-section avatar>
            <q-icon name="fa fa-house" color="indigo-4" />
          </q-item-section>

          <q-item-section> Inicio </q-item-section>
        </q-item>

        <q-item clickable v-ripple to="redacoes">
          <q-item-section avatar>
            <q-icon name="fa fa-sheet-plastic" color="indigo-4" />
          </q-item-section>

          <q-item-section> Redações </q-item-section>
        </q-item>

        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="fa fa-chart-simple" color="indigo-4" />
          </q-item-section>

          <q-item-section> Evolução </q-item-section>
        </q-item>
      </q-list>
    </q-scroll-area>
  </q-drawer>
</template>

<script setup>
import { ref } from 'vue';

const value = ref(false);
const miniState = ref(true);
const texto = ref();

const handleMouseOver = () => {
  miniState.value = false;
  if (!miniState.value) {
    texto.value = 'Escrever';
  }
};

const handleMouseOut = () => {
  miniState.value = true;
  if (miniState.value) {
    texto.value = '';
  }
};
</script>

<style scope lang="scss">
.q-btn {
  transition: transform 0.1s ease-in-out; /* Define a transição suave na propriedade transform */
}

.btn-expanded {
  align-content: flex-end;
  text-align: center;
  font-size: 1.2rem;
  width: 11rem;
  height: 4rem; /* Aumenta a escala do botão em 20% quando miniState for false */
}
</style>
