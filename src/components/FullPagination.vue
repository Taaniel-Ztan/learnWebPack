<template>
    <nav class="pagination is-centered" role="navigation" aria-label="pagination">
        <a class="pagination-previous" @click="$emit('goToPage', current-1)">Previous</a>
        <a class="pagination-next" @click="$emit('goToPage', current+1)">Next page</a>
        <ul class="pagination-list">
            <li v-if="current>2">
                <a class="pagination-link" aria-label="Goto page 1" @click="$emit('goToPage', 1)">1</a>
            </li>
            <li v-if="current>3">
                <span class="pagination-ellipsis">&hellip;</span>
            </li>
            <li v-if="current>1">
                <a class="pagination-link" :aria-label="'Goto page ' + current-1" @click="$emit('goToPage', current-1)">
                    {{current - 1}}
                </a>
            </li>
            <li>
                <a class="pagination-link is-current" :aria-label="'Page ' + current" aria-current="page">
                {{current}}
                </a>
            </li>
            <li v-if="current<info.pages">
                <a class="pagination-link" :aria-label="'Goto page ' + current+1" @click="$emit('goToPage', current+1)">
                    {{current+1}}
                </a>
            </li>
            <li v-if="current<info.pages-2">
                <span class="pagination-ellipsis">&hellip;</span>
            </li>
            <li v-if="current<info.pages-1">
                <a class="pagination-link" :aria-label="'Goto page ' + info.pages" @click="$emit('goToPage', info.pages)">
                {{info.pages}}
                </a>
            </li>
        </ul>
    </nav>
</template>

<script>
export default {
    props: ['info', 'current']
}
</script>

<style>
</style>