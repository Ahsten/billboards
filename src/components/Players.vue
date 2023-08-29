<script setup lang="ts">
import { ref } from 'vue';
import Picks from './Picks.vue';

interface Player {
    name: string,
    firstPick: string,
    secondPick: string
}

const newPlayer = ref("")
const players = ref<Player[]>([]);

function addPlayer(){
    players.value.push({name: newPlayer.value, firstPick: "", secondPick: ""});
    newPlayer.value = "";
}

function clearPlayers(){
    players.value = [];
}

</script>
<template>
    <div class="grid grid-auto-rows">
        <ul class="menu menu-sm">
            <li v-for="player in players" :key="player.name">
                <h2 class="menu-title text-accent text-lg">{{ player.name }}</h2>
                <ul>
                    <li class="text-xl">{{ player.firstPick }}</li>
                    <li class="text-xl">{{ player.secondPick }}</li>
                </ul>
            </li>
        </ul>
        <div class="divider"></div>
        <form @submit.prevent="addPlayer" class="join">
            <input v-model="newPlayer" class="input input-bordered join-item" placeholder="Add player...">
            <button class="btn btn-accent join-item">Add</button>
        </form>
        <div class="divider"></div>
        <div class="grid grid-rows-2 gap-2">
            <Picks :players="players"/>
            <button class="btn btn-accent w-full" @click="clearPlayers()">Clear Players</button>
        </div>
    </div>
</template>