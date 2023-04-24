<script>
import { store } from '../store';
import CardItem from './CardItem.vue';

export default {
    name: 'CardList',

    components: {
        CardItem,
    },

    data() {
        return {
            store,
        };
    }


}
</script>



<template>
    <section class="container">
        <div v-if="store.isLoading">loading...</div>
        <div v-else class="row">
            <!-- ciclo vfor per ciclare le card, importante mettere l'index -->
            <div v-for="(card, index) in store.people" :key="index" class="col-lg-6">
                <!-- inserisco il carditem con le props assegnate -->
                <CardItem :character="card" />
            </div>

        </div>
    </section>
</template>



<style lang="scss" scoped></style>