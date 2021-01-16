<template>
    <ul>
        <Listsitem 
            v-for="(item, index) in items" 
            :item="item"
            :key="index">
        </Listsitem>
        <!-- <li v-for="(item, index) in items" :key="index">
            {{ item.text }}
        </li> -->
    </ul>
</template>
<script>
    import Listsitem from "./Listsitem";
    export default {
        name: 'Lists',
        components: { Listsitem },
        props: ['items'],
    }
</script>
<style>
    
</style>