<template>
    <div>
        <h2>List of Crypto Coin</h2>
        <input type="number" min="1" max="6" v-model.number = "userCount">
        <button v-on:click = "doSomething"> Click me {{userCount}}</button>

        <table>
            <tr>
                <th>Symbol</th>
                <th>Name</th>
                <th>Price</th>
            </tr>

            <tr v-for="(u, index) in ApiData" :key="index">
                <td>{{u.symbol}}</td>
                <td>{{u.name}}</td>
                <td>{{u.current_price}}</td>
            </tr>
        </table>

    </div>
</template>

<script lang="ts">
import { Component, Vue} from "vue-property-decorator";
import axios, {AxiosResponse} from "axios";

type token = {
    name: string;
    symbol: string;
    current_price: number;

}

@Component
export default class JustTest extends Vue{
    userCount = 2;
 
    ApiData: Array<token> = []; 

    mounted(): void {
        console.log("This print when the justtest is mounted to the dom")
    }
    name():void{
        this.name
    }
    
    doSomething(): void {
       axios.request({
           method: "GET", 
           url: "https://api.coingecko.com/api/v3/coins/markets", 
           params: {
            vs_currency: "usd",
       },
       })
       .then((r:AxiosResponse) => r.data)
       .then((someData: Array<token>) => {
            console.log(someData);
            this.ApiData.splice(0);
            this.ApiData.push(...someData)
        });
        
    }
}
</script>

<style>

h2{
    margin: 2ex;
}

table{
    border: 2px solid black;
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
    background-color: lightskyblue;
}
table tr:nth-child(even){
    background-color: white;
}


</style>