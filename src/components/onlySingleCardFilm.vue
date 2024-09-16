<script>
export default {
    date() {

    },
    props: {
        card: Object
    }
}
</script>

<template>
<div>
    <h2>
        {{ card.title }}
    </h2>
    <h3>
        {{ card.original_title }}
    </h3>
    <h4>
        {{ card.original_language }}
    </h4>
    <h5>
        {{ card.vote_average }}
    </h5>

</div>
    
</template>

<style lang="scss" scoped>

</style>