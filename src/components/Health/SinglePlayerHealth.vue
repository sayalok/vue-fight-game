<template>
    <div class="small-6 columns">
        <h1 class="text-center">{{playerName}}</h1>
        <div class="healthbar">
            <div 
                class="healthbar text-center" 
                style="background-color: green; margin: 0; color: white;"
                id="{{playerHealth}}"
                :style="{ width:playerHealth + '%' }">
                {{ playerHealth }}
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        name: 'SinglePlayerHealth',
        props: ['playerName','playerHealth']
    }
</script>
<style>

</style>