<template>
    <div>
        <input type="search" v-model="search" class="search" placeholder="куда..."/>
        <ul >
            
            <li v-for="item in searchHendler" :key="item.id">
                <p>из {{item.departure_city}}</p>
                <p>в {{item.arrival_city}}</p>
                <p>с {{item.departure_date_time}}</p>
                <p>по {{item.arrival_date_time}}</p>
                <p>цена {{item.sele}}</p>
                
            </li>
            
        </ul>
    </div>
</template>
<script>
import {bilet} from './data/data';
export default{
    name:"App",
    data() {
        return{
            search:'',
            data:[]
        }
    },
    created() {
        this.data = bilet;
    },
    computed: {
        searchHendler(){
        return this.data.filter(elem => {
            return elem.arrival_city.toLowerCase().includes(this.search);
        });
        }
    }
};
</script>
<style>
    
</style>