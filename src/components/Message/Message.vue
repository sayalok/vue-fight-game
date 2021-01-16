<template>
    <section class="row log">
        <div class="small-12 columns">
            <Lists :items="logs"></Lists>
        </div>
	</section>
</template>
<script>
    import Lists from "../Lists/Lists";
    export default {
        name: 'Message',
        components: { Lists },
        props: ['logs'],
    }
</script>
<style>

</style>