<template>
    <button @click="$emit('prev')" class="button is-dark" :disabled="!info.prev">Prev</button>
    <button @click="$emit('next')" class="button is-dark" :disabled="!info.next">Next</button>
</template>

<script>
export default {
    props: ['info']

}
</script>

<style>

</style>