<template>
<div class="container">
    <section class="section">        
        <div class="field has-addons ">
            <p class="control">
                <input class="input" type="text" v-model="newItem" @keydown.enter="addItem()">
            </p>
            <p class="control">
                <button class="button" @click="addItem()">Add</button> 
            </p>
                     
      </div>
      <div class="content">
          <h1>All items</h1>
            <ul>
                <li v-for="item in items" :key="item.id">
                    {{ item.name }}
                    <input type="checkbox" v-model="item.done">
                    
                </li>
            </ul>

            <h1>Done items</h1>
            <ul>
                <li v-for="item in doneItems" :key="item.id">
                    {{ item.name }}
                    <input type="checkbox" v-model="item.done">                   
                </li>
            </ul>

            <h1>Not done items</h1>
            <ul>
                <li v-for="item in notDoneItems" :key="item.id">
                    {{ item.name }}
                    <input type="checkbox" v-model="item.done">                   
                </li>
            </ul>
        </div>
    </section>
</div>

</template>

<script>
export default {
    data(){
        return {   
            newItem: '',
            count: 0,
            items: [
                {name:'piim', done: true, id: 0},
                {name:'sai', done: false, id: 1},
                {name:'viin', done: true, id: 2},
                {name:'õlu', done: false, id: 3},
                ]
        }
    },
    methods: {
        addItem(){
            if(this.newItem.trim() != ''){            
                this.items.push({name:this.newItem, done: false, id: this.items.length});
            }
            this.newItem = '';
        }
    },
    computed: {
        doneItems(){
            return this.items.filter(item => item.done);
        },
        notDoneItems(){
            return this.items.filter(item => !item.done);
        },
    }
}
</script>

<style>

</style>