<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Blank</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Blank</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-input v-model="nome"></ion-input>
      <div>O nome é {{  nome  }}</div>

      <div><ion-button :disabled="valor == 18" @click="incrementa()">Adicionar</ion-button></div>
      
      <div>Sua idade {{ valor }}</div>

      <div v-if="valor == 18">Você se fudeu</div>
     

      <div>
        <p>Quer mudar de pagina?</p>
        <ion-button @click='router.push("/tarefas")'>Ir para tarefas</ion-button>
      </div>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import router from '@/router';
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonInput } from '@ionic/vue';
import { ref } from 'vue';


const valor = ref(0);
const nome = ref("");

const incrementa = () => {
  valor.value++;
}

</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
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
</style>
