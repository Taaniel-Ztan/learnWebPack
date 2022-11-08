<template>
    <div class="columns">
        <div class="column is-one-third has-text-centered">
            <b>{{clicks}} clicks</b>  
            <br>
            <b>{{cps}} clicks per second</b>  
            <img @click="clickClick()" :class="{'click': clickClass}" src="https://pngimg.com/uploads/astronaut/astronaut_PNG9.png">   
        </div>
        <div class="column">
            <button @click="upgrade(6969, 10)" class="button is-white" :disabled="clicks<10">Buy 0.1 cps for 10 clicks</button>     
            <br>
            <br>
            <button @click="upgrade(1, 100)" class="button is-white" :disabled="clicks<100">Buy 1 cps for 100 clicks</button> 
            <br>
            <br>
            <button @click="upgrade(10, 1000)" class="button is-white" :disabled="clicks<1000">Buy 10 cps for 1000 clicks</button>
            <br>  
            <br>    
            <button @click="upgrade(100, 10000)" class="button is-white" :disabled="clicks<10000">Buy 100 cps for 10000 clicks</button> 
            <br>
            <br>
            <button @click="upgrade(1000, 100000)" class="button is-white" :disabled="clicks<100000">Buy 1000 cps for 100000 clicks</button> 
            <br>
            <br>
            <button @click="upgrade(10000, 1000000)" class="button is-white" :disabled="clicks<1000000">Buy 10000 cps for 1000000 clicks</button> 
            <br>
            <br>
            <button @click="upgrade(100000, 10000000)" class="button is-white" :disabled="clicks<10000000">Buy 100000 cps for 10000000 clicks</button> 
            <br>
            <br>
            <button @click="upgrade(1000000, 100000000)" class="button is-white" :disabled="clicks<100000000">Buy 1000000 cps for 100000000 clicks</button> 
        </div>
    </div>

</template>

<script>
export default {
    created(){
        setInterval(()=>{
            this.clicks += this.cps;
            this.clicks = parseFloat(this.clicks.toFixed(1));


        }, 1000);
    },
    data(){
        return {
            clickClass: false,
            clicks: 0,
            cps: 0

        }
    },
    methods: {
        clickClick(){
            this.clicks++;
            this.clickClass = true;
            setTimeout(()=> {
                this.clickClass = false;
            }, 100);
        },
        upgrade(cps, cost){
            if(this.clicks >= cost){
                this.clicks -= cost;
                this.cps += cps;
            }
        }
    }

}


</script>

<style scoped>
    img.click {
        transform: scale(0.9);
    }
    b {
        color: white;
    }

</style>