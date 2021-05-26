<template>
        <div class="conversor">
            <h2>{{moedaA}} Para {{moedaB}}</h2>
            <input type="text" v-model="moedaA_value" v-bind:placeholder="moedaA">
            <input type="button" value="converter" v-on:click="converter()">
            <h2>{{moedaB_value}}</h2>
        </div>
</template>

<script>


export default {
    name: "Conversor",
    props: ["moedaA","moedaB"],
    data(){
        return{
            moedaA_value: "",
            moedaB_value:  0
        }
    },
    methods: {
        
        converter(){
            let de_para = this.moedaA+"_"+this.moedaB
            let url ="https://free.currconv.com/api/v7/convert?q="+de_para+"&compact=ultra&apiKey=f21945175f55fc0479be"
            fetch(url)
                .then(res=>{
                    return res.json()
                    })
                    .then(json=>{
                        console.log(" "+json[de_para].toString())
                        let cotacao = json[de_para];
                        console.log(cotacao)
                        this.moedaB_value = cotacao* parseFloat(this.moedaA_value)
                        this.moedaB_value = this.moedaB_value.toFixed(2)
                    })
        }
    }
}

</script>


<style scoped>
    .conversor{
        background-color: rgb(126, 123, 120);
        color: white;
        display: flex;
        flex-direction: column;
        margin: 10px;
        padding: 1em;
    }
    .conversor > * {
        margin: 3px;
    }
</style>