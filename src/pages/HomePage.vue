<template>
  <body class="my-body-desk desktop">
    <div class="my-tema-principal q-pa-md">
      <h4>Escreva sua redação</h4>
    </div>
    <EditorTextoVue />
  </body>
</template>

<script setup>
import EditorTextoVue from 'src/components/EditorTexto.vue';
</script>

<style scope lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Anton&family=Montserrat&display=swap');
$grey-9: $blue-grey-14;

.my-tema-principal {
  font-family: 'Anton', sans-serif;
  position: relative;
  text-align: center;
  color: $grey-9;
}
.my-editor-text {
}
</style>
