<template>
    <ion-page>
        <ion-header :translucent="true">
            <ion-toolbar>
                <ion-title>Tarefas</ion-title>
            </ion-toolbar>
        </ion-header>

        <ion-content :fullscreen="true">

       
            <ion-card>
                <ion-card-header>
                    <ion-card-title>Nova Tarefa</ion-card-title>
                </ion-card-header>

                <ion-card-content>
                    <ion-input
                        v-model="conteudoTarefa"
                        label="Nome da tarefa"
                        label-placement="floating"
                        :clear-input="true"
                        placeholder="Ex: Estudar Vue.js"
                        :error-text="erroTarefa"
                        :class="{'ion-invalid ion-touched': erroTarefa}"
                    ></ion-input>

                    <ion-button expand="block" fill="solid" color="primary" @click="adicionarTarefa">
                        <ion-icon slot="start" :icon="addOutline" />
                        Adicionar tarefa
                    </ion-button>
                </ion-card-content>
            </ion-card>

            <ion-card>
                <ion-card-header>
                    <ion-card-title>
                        Minhas Tarefas ({{ tarefaLista.length }})
                    </ion-card-title>
                </ion-card-header>

                <ion-card-content>

                    <ion-list>
                        <ion-item v-for="(tarefa, index) in tarefaLista" :key="index">
                            
                            <ion-icon slot="start" :icon="checkmarkCircleOutline" />

                            <ion-label>{{ tarefa }}</ion-label>

                            <ion-button
                                slot="end"
                                fill="clear"
                                color="danger"
                                @click="removerTarefa(index)"
                            >
                                <ion-icon :icon="trashOutline" />
                            </ion-button>

                        </ion-item>
                    </ion-list>

                    <p v-if="tarefaLista.length === 0" class="ion-text-center ion-padding">
                        Nenhuma tarefa cadastrada.
                    </p>

                </ion-card-content>
            </ion-card>

             <div>
        <p>Quer ir para as home?</p>
        <ion-button @click='router.push("/home")'>Ir para home</ion-button>
      </div>
        </ion-content>
    </ion-page>
</template>

<script setup lang="ts">
import router from '@/router';
import {
    IonCard, IonCardContent, IonCardHeader, IonCardTitle,
    IonContent, IonHeader, IonPage, IonTitle, IonToolbar,
    IonInput, IonButton, IonIcon, IonList, IonItem, IonLabel
} from '@ionic/vue';

import { ref, computed } from 'vue';
import { addOutline, trashOutline, checkmarkCircleOutline } from 'ionicons/icons';

const tarefaLista = ref<string[]>([]);
const conteudoTarefa = ref("");

const erroTarefa = computed(() =>
    !conteudoTarefa.value.trim() ? "Campo obrigatório" : ""
);

const adicionarTarefa = () => {
    if (conteudoTarefa.value.trim() === "") return;

    tarefaLista.value.push(conteudoTarefa.value);
    conteudoTarefa.value = "";
};

const removerTarefa = (index: number) => {
    tarefaLista.value.splice(index, 1);
};
</script>

<style scoped>
ion-card {
    margin: 16px;
}
</style>