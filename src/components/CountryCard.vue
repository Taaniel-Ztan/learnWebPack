<template>
    <div class="card">
        <router-link :to="'/countries/' + country.Slug">
            <header class="card-header has-background-primary">
                <p class="card-header-title">{{country.Country}}</p>
                <figure class="image is-64x64">
                    <img :src="'https://countryflagsapi.com/png/' + country.CountryCode">
                </figure>
            </header>
        </router-link>
        <div class="card-content">
            <div class="content">
                <b>New Confirmed:</b> {{country.NewConfirmed}}<br>
                <b>New Deaths:</b> {{country.NewDeaths}}<br>
                <!-- <b>New Recovered:</b> {{country.NewRecovered}}<br> -->
                <b>Total Confirmed:</b> {{country.TotalConfirmed}}<br>
                <b>Total Deaths:</b> {{country.TotalDeaths}}<br>
                <!-- <b>Total Recovered:</b> {{country.TotalRecovered}}<br> -->
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['country']
}
</script>

<style>
    .card {
        height:100%;
    }
</style>