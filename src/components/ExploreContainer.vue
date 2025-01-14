<template>
  <div id="container">
    <ion-item class="box">
      <ion-input
        ref="input1"
        class="custom"
        v-model="input1Value"
        placeholder="Введите текст"
      ></ion-input>
    </ion-item>
    <ion-button @click="transferText">Перенести текст</ion-button>

    <ion-modal :is-open="isOpen">
      <ion-header>
        <ion-toolbar>
          <ion-title>Modal</ion-title>
          <ion-buttons slot="end">
            <ion-button @click="setOpen(false)">Close</ion-button>
          </ion-buttons>
        </ion-toolbar>
      </ion-header>
      <ion-content class="ion-padding">
        <p>
         {{ input1Value }}
        </p>
      </ion-content>
    </ion-modal>
  </div>
</template>

<script setup lang="ts">
  import { ref } from "vue";
  import { IonButton, IonInput, IonModal } from "@ionic/vue";

  // Переменные для хранения значений
  const input1Value = ref("");

  const isOpen = ref(false);

  const setOpen = (open: boolean) => (isOpen.value = open);

  // Функция переноса текста
  const transferText = () => {
    setOpen(true)
  }
</script>

<style scoped>
#container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh; /* Высота окна */
  padding: 16px;
  box-sizing: border-box;
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  color: #8c8c8c;
  margin: 0;
}

#container a {
  text-decoration: none;
}
ion-input.custom {

}
ion-item.box{
  margin-bottom: 30px;
}

</style>
