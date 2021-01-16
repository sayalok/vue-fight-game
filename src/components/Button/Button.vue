<template>
    <button 
        :id="id"
        @click="clickEvent">
        {{value}}
    </button>
</template>
<script>
    export default {
        name: 'Button',
        props: ['id','value'],
        methods: {
            clickEvent: function () {
                this.$emit('clickEvent')
            }
        },
    }
</script>
<style>

</style>