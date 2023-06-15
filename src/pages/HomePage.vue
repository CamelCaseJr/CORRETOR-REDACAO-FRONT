<template>
  <body class="my-body-desk desktop">
    <div class="my-tema-principal q-pa-md">
      <h4>Escreva sua redação</h4>
    </div>
    <div class="my-editor-text q-pa-md q-gutter-sm">
      <q-editor
        @submit.prevent.stop="onSubmit"
        @reset.prevent.stop="onReset"
        v-model="editor"
        height="50vh"
        :dense="$q.screen.lt.md"
        :definitions="{
          save: {
            tip: 'Save your work',
            icon: 'save',
            label: 'Save',
            handler: saveWork,
          },
        }"
        :toolbar="[
          [
            {
              label: $q.lang.editor.align,
              icon: $q.iconSet.editor.align,
              fixedLabel: true,
              list: 'only-icons',
              options: ['left', 'center', 'right', 'justify'],
            },
            {
              label: $q.lang.editor.align,
              icon: $q.iconSet.editor.align,
              fixedLabel: true,
              options: ['left', 'center', 'right', 'justify'],
            },
          ],
          ['bold', 'italic', 'strike', 'underline', 'subscript', 'superscript'],
          ['token', 'hr', 'link', 'custom_btn'],
          ['print', 'fullscreen'],
          ['save'],
          [
            {
              label: $q.lang.editor.formatting,
              icon: $q.iconSet.editor.formatting,
              list: 'no-icons',
              options: ['p', 'h1', 'h2', 'h3', 'h4', 'h5', 'h6', 'code'],
            },
            {
              label: $q.lang.editor.fontSize,
              icon: $q.iconSet.editor.fontSize,
              fixedLabel: true,
              fixedIcon: true,
              list: 'no-icons',
              options: [
                'size-1',
                'size-2',
                'size-3',
                'size-4',
                'size-5',
                'size-6',
                'size-7',
              ],
            },
            {
              label: $q.lang.editor.defaultFont,
              icon: $q.iconSet.editor.font,
              fixedIcon: true,
              list: 'no-icons',
              options: [
                'default_font',
                'arial',
                'arial_black',
                'comic_sans',
                'courier_new',
                'impact',
                'lucida_grande',
                'times_new_roman',
                'verdana',
              ],
            },
            'removeFormat',
          ],
          ['quote', 'unordered', 'ordered', 'outdent', 'indent'],

          ['undo', 'redo'],
          ['viewsource'],
        ]"
        :fonts="{
          arial: 'Arial',
          arial_black: 'Arial Black',
          comic_sans: 'Comic Sans MS',
          courier_new: 'Courier New',
          impact: 'Impact',
          lucida_grande: 'Lucida Grande',
          times_new_roman: 'Times New Roman',
          verdana: 'Verdana',
        }"
      />
    </div>
    <div class="my-editor-text q-pa-md q-gutter-sm">
      <q-btn
        @click="onSubmit"
        type="submit"
        color="secondary"
        label="Corrigir"
      />
      <q-btn
        @click="onReset"
        type="reset"
        flat
        color="blue-grey-14"
        label="reset"
      />
    </div>
  </body>
</template>

<script setup>
import { ref } from 'vue';
import { useQuasar } from 'quasar';
const $q = useQuasar();

const editor = ref('');

const onSubmit = () => {
  editor.value.trim();
  if (editor.value.length === 0 || editor.value === '<br>') {
    console.log(editor.value);
    $q.notify({
      color: 'negative',
      message: 'Você precisa escrever algo para enviar!',
    });
  } else {
    $q.dialog({
      title: 'Confirm',
      message: 'Realmente deseja enviar para correção?',
      cancel: true,
      persistent: true,
    })
      .onOk(() => {
        // console.log('OK')
        console.log(editor.value);
        $q.notify({
          message: 'Saved your text to local storage',
          color: 'green-4',
          textColor: 'white',
          icon: 'cloud_done',
        });
        limparTexto();
      })
      .onCancel(() => {
        // console.log('Cancel')
      })
      .onDismiss(() => {
        // console.log('I am triggered on both OK and Cancel')
      });
  }
};

const limparTexto = () => {
  editor.value = '';
};

const onReset = () => {
  $q.dialog({
    title: 'Confirm',
    message: 'Realmente deseja limpar o texto?',
    cancel: true,
    persistent: true,
  })
    .onOk(() => {
      // console.log('OK')
      console.log(editor.value);
      $q.notify({
        message: 'Saved your text to local storage',
        color: 'green-4',
        textColor: 'white',
        icon: 'cloud_done',
      });
      limparTexto();
    })
    .onCancel(() => {
      // console.log('Cancel')
    })
    .onDismiss(() => {
      // console.log('I am triggered on both OK and Cancel')
    });
};

const saveWork = () => {
  editor.value.trim();
  if (editor.value.length === 0 || editor.value === '<br>') {
    console.log(editor.value);
    $q.notify({
      color: 'negative',
      message: 'Você precisa escrever algo para enviar!',
    });
  } else {
    $q.notify({
      message: 'Saved your text to local storage',
      color: 'green-4',
      textColor: 'white',
      icon: 'cloud_done',
    });
  }
};
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
