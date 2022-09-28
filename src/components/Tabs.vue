<template>
<div class="tabs">
  <ul>
        <!-- <li class="is-active"><a>Pictures</a></li> -->
        <li @click="active=index" :class="{'is-active': current===link.path}" v-for="(link, index) in links" :key="index">
            <router-link :to="link.path">{{link.name}}</router-link>
            </li>
        </ul>
    </div>
</template>

<script>
export default { 
    props: ['links', 'current'],   
}

</script>

<style>

</style>