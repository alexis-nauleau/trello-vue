<script setup lang="ts">
import type { Task } from '@/type';
defineProps<{ task: Task; columnColor: string }>();
</script>

<template>
    <div class="bg-white rounded shadow min-w-[450px] p-2 mb-2">
        <input type="text" class="min-w-[400px]" @keyup.enter="($event.target as HTMLInputElement).blur()" v-model="task.title">
        
        <button :style="{ backgroundColor: columnColor }" class="rounded-lg px-2 py-1 text-white font-bold h-4 w-20">
           
        </button>
    </div>
</template>
