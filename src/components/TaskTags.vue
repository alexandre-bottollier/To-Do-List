<script setup>

import { ref,onMounted,onUpdated } from 'vue';

const props = defineProps({
    trigger: {
        type: Boolean,
        required: true,
    },
})

const input = ref();

const tags = ref([]);

const emits = defineEmits(['tags']);

onUpdated(() => {
    tags.value = input.value.value.split(' ');

    if (props.trigger===true) {
    input.value.value = '';

    emits('tags', tags.value);

}
})


</script>



<template>
    
    <input 
    type="text"
    placeholder="Tags"
    size="5"
    ref="input"
    />

</template>



<style scoped>
input {
    padding: 10px;
    border-radius: 5px;
    margin: 5px;
}
</style>