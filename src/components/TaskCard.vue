<script setup>
import { ref,onMounted,onUpdated } from 'vue';

const props = defineProps({
    title: {
        type: String,
        required: true,
    },

    id: {
        type: Number,
        required: true,
    },

    tags: {
        type: Array,
        required: false,
    }
})

const emits = defineEmits(["removeTask"]);


function removeTask () {
    emits('removeTask', props.id);
}

const isTicked = ref(false);
// const tagsString = ref();
// onUpdated (() => {
//     tagsString.value = props.tags.toString();
// })

</script>

<template>

    <div class="card">
        <p class="card__title" :class="isTicked ? 'card__title-overline' : ''">{{ title }}</p>
        <!-- <p class="card__tags">{{ tagsString }}</p> -->
        <div class="card-utils">
            <input type="checkbox" @click="isTicked = !isTicked">
            <button type="button" @click="removeTask" >🗑️</button>
        </div>
    </div>



</template>


<style scoped>
.card {
    display: flex;
    width: 200px;
    justify-content: space-between;
    align-items: center;

    border: 2px solid gray;
    margin-bottom: 20px;
    border-radius: 10px;
    background-color: whitesmoke;
    padding-left: 10px;
    padding-right: 10px;

}

.card__title-overline{
    text-decoration: line-through;
}


</style>