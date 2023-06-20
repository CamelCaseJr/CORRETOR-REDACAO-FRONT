<template>
  <div>
    <q-card>
      <q-card-section>
        <div class="q-pa-md" style="max-width: 300px">
          <form
            @submit.prevent.stop="onSubmit"
            @reset.prevent.stop="onReset"
            class="q-gutter-md"
          >
            <q-input
              ref="nameRef"
              filled
              v-model="name"
              label="Your name *"
              hint="Name and surname"
              lazy-rules
              :rules="nameRules"
            />

            <q-input
              ref="ageRef"
              filled
              type="number"
              v-model="age"
              label="Your age *"
              lazy-rules
              :rules="ageRules"
            />

            <q-toggle v-model="accept" label="I accept the license and terms" />

            <div>
              <q-btn label="Submit" type="submit" color="primary" />
              <q-btn
                label="Reset"
                type="reset"
                color="primary"
                flat
                class="q-ml-sm"
              />
            </div>
          </form>
        </div>
      </q-card-section>
    </q-card>
  </div>
</template>

<script setup></script>

<style></style>
