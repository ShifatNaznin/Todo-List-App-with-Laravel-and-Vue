<template>
    <div class="todoList">
        <div class="heading">
           <h2 id="title">TODO LIST</h2>
           <add-list-item
            v-on:reloadList="getList()"
           />
        </div>
        <view-list-item 
        :items="items"
        v-on:reloadList="getList()"
        />
    </div>
</template>

<script>

import addListItem from './addListItem.vue'
import viewListItem from './viewListItem.vue'
export default {
    components: {
        addListItem,
        viewListItem,
    },
    data: function(){
     return{
         items:[]
     }
    },
    methods: {
        getList(){
            axios.get('api/items')
            .then(response=>{
                this.items = response.data
            })
            .catch(error=>{
                console.log(error);
            })
        }
    },
    created(){
        this.getList();
    }
}
</script>

<style scoped>
.todoList {
 width: 550px;
 margin: auto;
}

.heading{
    background: #2b373a;
    padding: 10px;
}

#title{
    text-align: center;
    color:#5abae7;
}
</style>