<template>
    <input type="text" class="input" v-model="search" @input="filter">
    <simple-pagination @prev="prev()" @next="next()" :info="info"></simple-pagination>
    <full-pagination :info="info" :current="currentPage" @goToPage="goToPage"></full-pagination>
    <div class="columns is-multiline">
        <div v-for="character in characters" :key="character.id" class="column is-one-quarter">
            <character-card :character="character"></character-card>
        </div>   
    </div>
<html class="contact-bg"></html>


</template>

<script>
import axios from 'axios';
import CharacterCard from '../components/CharacterCard.vue';
import SimplePagination from '../components/SimplePagination.vue';
import FullPagination from '../components/FullPagination.vue';
export default {
  components: { CharacterCard, SimplePagination, FullPagination },
    created(){
        this.getPage('https://rickandmortyapi.com/api/character');
    },
    mounted(){
        // window.addEventListener('scroll', evt => {
        //     if(window.scrollY+window.innerHeight > document.body.scrollHeight*0.7 && this.hasLoaded){
        //         this.next();
        //     }
        // });
    },
    data(){
        return {
            info: {},
            characters: [],
            currentPage: 1,
            hasLoaded: true,
            search: '',
            searchTimeout: null,
        }
    },
    methods: {
        getPage(url){
            axios.get(url).then(res => {
                console.log(res.data);
                this.info = res.data.info;
                this.characters = res.data.results;
                this.hasLoaded = true;
            });
        },
        prev(){
            this.currentPage--;
            this.getPage(this.info.prev);
        },
        next(){
            this.hasLoaded=false;
            this.currentPage++;
            this.getPage(this.info.next);
        },
        goToPage(page){
            this.currentPage=page;
            if(this.search){
                this.getPage('https://rickandmortyapi.com/api/character?page=' + page + '&name=' + this.search);
            } else {
                this.getPage('https://rickandmortyapi.com/api/character?page=' + page);
            }
        },
        filter(evt){
            clearTimeout(this.searchTimeout);
            this.searchTimeout = setTimeout(() => {
                this.currentPage = 1;
                this.getPage('https://rickandmortyapi.com/api/character?name=' + this.search);
            }, 1000);
            
        }
    }
}
</script>

<style>
</style>