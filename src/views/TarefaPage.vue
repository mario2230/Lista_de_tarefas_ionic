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
                <h2>Quantidades de tarefas {{  tarefaQuantidade  }}</h2>
            </div>
            <ion-input v-model="conteudoTarefa" placeholder="Digite a sua tarefa"></ion-input>
            <ion-button @click="adicionarTarefa()">Adicionar a tarefa</ion-button>
            <ion-button @click='router.push("/home")'>Ir para pagina inicial</ion-button>

            <div v-for="(tarefa, index) in tarefaLista" :key="index">
             <ion-item><ion-label>  {{ tarefa }} <ion-button @click="removerTarefa(index)">Remover</ion-button> </ion-label></ion-item> 
            </div>
            

            <div v-if=" tarefaQuantidade === 0">
                Nenhuma tarefa cadastrada. Adicione a primeira!
            </div>
        </ion-content>
    </ion-page>
</template>


<script setup lang="ts"> 
import router from '@/router';  
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonInput, IonButton } from '@ionic/vue';
import { ref } from 'vue';

const tarefaQuantidade = ref(0);
const tarefaLista = ref<string[]>([]);
const conteudoTarefa = ref("");

const removerTarefa = (index:number) => {
    tarefaLista.value.splice(index, 1)
    tarefaQuantidade.value--;
}

const adicionarTarefa = () => {

    if(conteudoTarefa.value.trim() === "") {
        return
    }

    tarefaLista.value.push(conteudoTarefa.value);

    tarefaQuantidade.value++;

    conteudoTarefa.value = "";
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