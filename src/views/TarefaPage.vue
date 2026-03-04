<template>
    <ion-page>
        <ion-header :translucent="true">
            <ion-toolbar>
                <ion-title>Tarefas</ion-title>
            </ion-toolbar>
        </ion-header>


        <ion-content :fullscreen="true">
            <div>
                <h1>Suas tarefas</h1>
                <h2>Quantidades de tarefas {{  tarefa  }}</h2>
            </div>
            <ion-input @click="adicionarTarefa()">Tarefa ++</ion-input>
            <ion-button @click='router.push("/home")'>Ir para pagina inicial</ion-button>
        </ion-content>
    </ion-page>
</template>


<script setup lang="ts"> 
import router from '@/router';  
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonInput } from '@ionic/vue';
import { ref } from 'vue';


const tarefa = ref(0);

const adicionarTarefa = () => {
    tarefa.value++;
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