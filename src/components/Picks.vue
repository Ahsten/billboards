<script setup lang="ts">

interface Player {
    name: string,
    firstPick: string,
    secondPick: string
}

const props = defineProps<{
    players: Player[]
}>()

</script>
<template>
    <button class="btn btn-accent w-full" onclick="pick_modal.showModal()">Make Picks</button>
    <dialog id="pick_modal" class="modal">
        <form method="dialog" class="modal-box">
            <ul>
                <li v-for="player in props.players" :key="player.name">
                    <h2 class="card-title center">{{ player.name }}</h2>
                    <div class="form-control">
                        <label class="label">
                            <span class="label-text">First Pick</span>
                        </label>
                        <input v-model="player.firstPick" type="text" placeholder="First Pick" class="input input-bordered w-full"/>
                    </div>
                    <div class="form-control">
                        <label class="label">
                            <span class="label-text">Second Pick</span>
                        </label>
                        <input v-model="player.secondPick" type="text" placeholder="Second Pick" class="input input-bordered w-full"/>
                    </div>
                </li>
            </ul>
            <div class="modal-action">
                <button class="btn btn-accent">Make Picks</button>
            </div>
        </form>
    </dialog>
</template>