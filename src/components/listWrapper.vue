<template>
    <div class="inputWrapper">
        <input type="text" autofocus v-model="query" placeholder="search NASA database ...">
    </div>
    <div class="listWrapper">
        <div v-for="item in data" :key="item">
            <ListItems :item="item"/> 
            
        </div>
    </div>
    <div v-if="data.length === 0 && isLoading === false" class="noData">Data could not be founded ...</div>
    <div v-if="isLoading === true" class="noData">
        <Loading/>
    </div>
</template>
<script>
import ListItems from './listItems.vue';
import Loading from './loading.vue';

export default {
    name: 'listWrapper',
    components: {
        Loading,
        ListItems
    },
    data() {
        return {
            query: '',
            data: [],
            isLoading: false
        }
    },
    methods: {
        fetchData(query) {
            this.isLoading = true;
            fetch ('https://images-api.nasa.gov/search?q='+query)
            .then((result)=>result.json())
            .then((data)=>{
                this.isLoading = false
                console.log(data)
                this.data = data.collection.items
            })
        },
    },
    watch: {
        query(newVal) {
            if(newVal.length > 2) {
                this.fetchData(newVal)
            } else {
                this.data = []
            }
        }
    }
    
}
</script>
<style scoped>
.inputWrapper {
    width: 100%;
    display: flex;
    margin-bottom: 30px;
}
.inputWrapper input{
    width: 100%;
    height: 20px;
    display: flex;
    padding: 8px 16px;
    border: none;
    outline: none;
    border-radius: 10px;
    
}
.listWrapper {
    display: flex;
    justify-content: center;
    gap: 10px;
    flex-wrap: wrap;
}
.noData {
    text-align: center;
    width: 100%;
    font-size: 20px;
    color: aqua;
}
    
</style>