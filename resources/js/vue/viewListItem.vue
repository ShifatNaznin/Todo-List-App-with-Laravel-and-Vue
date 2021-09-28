<template>
    <div>
        
        <div v-for="(item,index) in items" :key="index">
           <list-item
           :item="item"
           class="item"
           v-on:itemchanged="$emit('reloadList')"
           />
        </div>
        
    </div>
</template>

<script>
import listItem from "./listItem.vue"
export default {
    props: ['items'], 
    components: {
        listItem
    }
}
</script>

<style scoped>
.item{
    background: #2b373a;
    padding: 5px;
    margin-top: 5px;
    color: #5abae7;
    border: 1px solid #939494;
    border-radius: 5px;
    height: 30px;
    font-size: 20px;
}
</style>