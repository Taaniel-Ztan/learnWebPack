<template>
    <tabs :links="$router.getRoutes()" :current="$route.path"></tabs>
    <div class="container">
        <section class="section">
            <router-view></router-view>
        </section>
    </div>
</template>

<script>
import Tabs from './components/Tabs.vue'
export default {
    components: { Tabs },
    created(){
        console.log(this.$router.getRoutes());
    }
}
</script>

<style>
</style>