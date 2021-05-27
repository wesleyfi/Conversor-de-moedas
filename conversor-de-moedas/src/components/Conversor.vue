<template>
        <div class="conversor">
            <h2> Dodge Para BRL</h2>
            
                <input type="text"  v-model="doge_value" placeholder="Valor em DogeCoin">
                <input type="button" value="converter" v-on:click="converter()">
                <h2>{{real_value}}</h2>
                <h3 >{{carregando}}</h3>
            
            
        </div>
</template>

<script>


export default {
    name: "Conversor",
    //props: ["moedaA","moedaB"],
    data(){
        return{
            //v-model="" v-bind:placeholder=""
           // moedaA_value: "",
            //moedaB_value:  0
            doge_value: "",
            real_value:0,
            carregando: ""
        }
    },
    mounted(){
        if(document.readyState== "complete"){
            this.isloaded=false;
        }else{
            this.isloaded=true;
        }
    },
    methods: {
        
        converter(){
            this.carregando="carregando"
            //let de_para = this.moedaA+"_"+this.moedaB
            /*
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
                    */
                let url = "https://chain.so/api/v2/get_price/DOGE"
                fetch(url)
                    .then(res => {
                        this.carregando = ""
                        return res.json()
                        
                    })
                    .then(json => {
                        let i;
                        var preco
                        for(i=0; i<=3; i++){
                           if(json["data"].prices[i].price_base=="USD"){

                                preco = json["data"].prices[i].price;
                        
                                console.log("moeda "+json["data"].prices[i].price_base)

                           } 
                        }
                        let url ="https://free.currconv.com/api/v7/convert?q=USD_BRL&compact=ultra&apiKey=f21945175f55fc0479be"
                        fetch(url)
                        .then(res=>{
                        return res.json()
                        })
                        .then(json=>{
                        let cotacao = json["USD_BRL"];
                        console.log(preco*cotacao)
                        this.real_value = ((preco * cotacao)*parseFloat(this.doge_value)).toFixed(2)
                        
                        })
                        
                        })
        }
    }
}

</script>


<style scoped>
    * {
        border:none;      
        border-radius: 10px;  
    }
    .conversor{
        background-color: rgb(30, 101, 119);
        color: white;
        display: flex;
        flex-direction: column;
        margin: 10px;
        padding: 1em;
    }
    .conversor > * {
        margin: 3px;
        text-align: center;
    }
</style>