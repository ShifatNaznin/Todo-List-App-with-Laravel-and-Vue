<template>
    <div class="addItem">
        <input type="text" v-model="item.name">
        <button type="button" @click="addItem()"
        :class="[item.name ? 'active' : 'inactive', 'plus']"> Add</button>
    </div>
</template>

<script>
export default {
    data: function(){
        return{ 
            item:{
                name: ""
            }
        }
    },
    methods:{
        addItem(){
           if(this.item.name == ""){
               return;
           }

           axios.post('api/item/store',{
               item: this.item
           })      
           .then(response =>{
               if(response.status == 201){
                   this.item.name = "";
                   this.$emit('reloadList');
               }
           })
           .catch(error => {
                console.log(error);
           })
        }
    }
}
</script>

<style scoped>
.addItem{
    display: flex;
    justify-content: center;
    align-items: center;
} 
input{
    background: #f7f7f7;
    border: 0px;
    outline: none;
    padding: 5px;
    margin-right: 10px;
    width: 100%;
    height: 30px;
    border-radius: 5px;
}

.plus{
    font-size:20px;

}
.active{
    color: #fff;
    background-color: #00ce67;
    border-color: #00ce67;
    width: 150px; 
    height: 40px;
    border-radius: 5px;
}

.inactive{
    color: #fff;
    background-color: #5abae7;
    border-color: #5abae7;
    width: 150px; 
    height: 40px;
    border-radius: 5px;
}


</style>