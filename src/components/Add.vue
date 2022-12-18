<template>
<Header/>
    <h1>Hello User, Welcome on Add Restaurant Page</h1>
    <form class="add">
        <input type="text" name="name" placeholder="Enter name" v-model="restaurant.name"/>
        <input type="text" name="contact" placeholder="Enter contact" v-model="restaurant.contact"/>
        <input type="text" name="address" placeholder="Enter address" v-model="restaurant.address"/>
    <button type="button" v-on:click="addRestaurant">Add new Restaurant</button>
    </form>
</template>
<script>
import Header from './Header.vue'
import axios from 'axios'
export default {
    name:'Add',
    components:{
        Header
    },
    data(){
        return  {
            restaurant: {
                name:'',
                contact:'',
                address:''
            }
        }
    },
    methods:{
        async addRestaurant()
        {
            console.warn(this.restaurant)
            const result = await axios.post("http://localhost:3000/restaurant",{
                name:this.restaurant.name,
                contact:this.restaurant.contact,
                address:this.restaurant.address,
            });
            if(result.status==201)
            {
                this.$router.push({name:'Home'});
            }
            console.warn('result',result)
        }
    },
    // mounted()
    // {
    //     let user = localStorage.getItem('user-info');
    //     if(!user)
    //     {
    //         this.$router.push({name:'SignUp'})
    //     }
    // }
}
</script>
