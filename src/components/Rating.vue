<template>
    <p @click="$emit('handleClick', rating)">
       {{ '️️⭐️'.repeat(rating) }}
    </p>
</template>

<script>
    export default {
        props: {
            rating: Number
        }
    }
</script>

<style lang="scss" scoped>

</style>
