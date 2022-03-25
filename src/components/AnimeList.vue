<template>
    <div>
        <h2>List of Animes</h2>
        <input type="number" min="1" max="6" v-model.number = "userCount">
        <button v-on:click = "doSomething">  Click me {{userCount}}</button>
        

        <table>
            <tr>
                <th>Anime ID</th>
                <th>Anime Name</th>
                <th>Anime Picture</th>
            </tr>

            <tr v-for="(u, index) in ApiData" :key="index">
                <td>{{u.anime_id}}</td>
                <td>{{u.anime_name}}</td>
                <td>
                    <img v-bind:src = "u.anime_img">
                </td>     
            </tr>
        </table>

    </div>
</template>

<script lang="ts">
import { Component, Vue} from "vue-property-decorator";
import axios, {AxiosResponse} from "axios";




type RUResponse = {
    data: Array<items>
}

type items = {
    anime_id: number;
    anime_name: string;
    anime_img: string;
}

@Component
export default class JustTest extends Vue{
    userCount = 2;
 
    ApiData: Array<items> = []; 

    mounted(): void {
        console.log("This print when the justtest is mounted to the dom")
    }
    
    
    doSomething(): void {
       axios.request({
           method: "GET", 
           url: "https://anime-facts-rest-api.herokuapp.com/api/v1", 
           params: {
            limits:this.userCount,
       },
       })
       .then((r:AxiosResponse) => r.data)
       .then((someData: RUResponse) => {
            console.log(someData.data);
            this.ApiData.splice(0);
            this.ApiData.push(...someData.data)
        });
        
    }
}
</script>

<style>

h2{
    margin: 2ex;
}

table{
    border: 2px solid blue;
}

table tr{
    background-color: lightblue;
}

table tr :first-child{
    color: black;
}
table tr :last-child{
    color: black;
}

table tr:nth-child(odd){
    background-color: lightgreen;
}
table tr:nth-child(even){
    background-color: white;
}


</style>