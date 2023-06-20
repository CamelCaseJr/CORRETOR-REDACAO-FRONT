<template>
  <body class="my-body">
    <section class="fixed-center shadow-2 area-login">
      <div class="q-pa-md" style="max-width: 300px">
        <form
          @submit.prevent.stop="onSubmit"
          @reset.prevent.stop="onReset"
          class="q-gutter-md"
        >
          <q-input
            ref="nameRef"
            color="pink-10"
            filled
            v-model="name"
            label="Seu nome *"
            hint="Name and surname"
            lazy-rules
            :rules="nameRules"
          />

          <q-input
            v-model="password"
            filled
            :type="isPwd ? 'password' : 'text'"
            hint="Password with toggle"
          >
            <template v-slot:append>
              <q-icon
                :name="isPwd ? 'visibility_off' : 'visibility'"
                class="cursor-pointer"
                @click="isPwd = !isPwd"
              />
            </template>
          </q-input>

          <div class="q-pl-xl">
            <q-btn label="Submit" type="submit" color="grey-9" />
            <q-btn
              label="Reset"
              type="reset"
              color="green-6"
              flat
              class="q-ml-sm"
            />
          </div>
        </form>
      </div>
    </section>
  </body>
</template>

<script setup>
import { ref } from 'vue';

const isPwd = ref(true);
</script>

<style scope lang="scss">
$cor: $dark;
$verde-9: $teal-9;
$segundo: $secondary;
$grey-1: $grey-1;
$grey-3: $grey-3;
$grey-4: $grey-4;
$grey-9: $grey-9;
$grey-10: $grey-10;
.my-body {
  width: 100%;
  height: 100vh;
  background: linear-gradient(120deg, $grey-1, $grey-3, $grey-4);
}

.area-login {
  background-color: transparent; /* Define o fundo como transparente */
  border: 1px solid $verde-9; /* Adiciona uma borda de 1px */
  box-shadow: 0 0 0 1px $verde-9; /* Adiciona uma sombra de 1px para criar a linha */
  width: 300px; /* Defina a largura desejada para o card */
  height: 250px;
  border-radius: 10px;
}
</style>
