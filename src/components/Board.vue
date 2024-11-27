<script setup lang="ts">
import type { Column } from '@/type';
import Draggable from 'vuedraggable';
import Tasks from './Tasks.vue';
import { useLocalStorage } from "@vueuse/core";

const columns = useLocalStorage<Array<Column>>('columns', [
    {
        id: 1,
        title: "A venir",
        background: "#FFFF00", 
        tasks: [
            {
                id: 1,
                title: "Maquetter des interfaces utilisateur web et web mobile",
                content: "Utiliser figma",
            },
            {
                id: 2,
                title: "Réaliser des interfaces utilisateur et statique web ou web mobile",
                content: "Utiliser Html, CSS, JS",
            },
            {
                id: 3,
                title: "Développer la partie dynamique des interfaces utilisateur web ou web mobile",
                content: "Utiliser Vue JS",
            },
            {
                id: 4,
                title: "Mettre en place une base de données relationnelles",
                content: "Utiliser SQL",
            },
            {
                id: 5,
                title: "Développer des composants d’accès aux données SQL et NoSQL",
                content: "Utiliser PHP",
            },
            {
                id: 6,
                title: "Développer des composants métiers côté serveurs",
                content: "Utiliser Next JS",
            },
        ]
    },
    {
        id: 2,
        title: "En cours",
        background: "#FFA500", 
        tasks: []
    },
    {
        id: 3,
        title: "Terminées",
        background: "#008000", 
        tasks: []
    },
]);
</script>

<template>
    <Draggable v-model="columns" group="columns" item-key="id" class="flex items-start space-x-2 mt-11" :animation="150">
        <template #item="{ element: column }">
            <div class="bg-gray-50 rounded shadow min-w-[480px] p-1 rel">
                <header class="font-bold mb-5 text-center">{{ column.title }}</header>
               
                <button :style="{ backgroundColor: column.background }" class="rounded-lg px-4 py-2 mb-3 text-white font-bold w-20 h-4 pos">
                   
                </button>
                <Draggable v-model="column.tasks" group="tasks" item-key="id" class="mt-2">
                    <template #item="{ element: task }">
                        <Tasks :task="task" :columnColor="column.background" />
                    </template>
                </Draggable>
            </div>
        </template>
    </Draggable>
</template>

<style scoped>
.pos {
    position: absolute;
    top: 15px;
    right: 25px;
}

.rel {
    position: relative;
}
</style>
