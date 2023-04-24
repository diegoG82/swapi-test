
<script>
import { store } from '../store';
export default {
    name: 'AppSearch',
    // dichiaro emits con questa sintassi
    emits: ['search'],
    data() {
        return {
            store
        }
    }
}
</script>




<template>
    <section class="container">
        <form @submit.prevent="">
            <div class="d-flex mb-5">
                <!-- nell'input inserisco il vmodel per interagire con il searchtext vuoto inserito nello store -->
                <input type="text" class="form-control me-3" placeholder="Search characters" v-model="store.searchText">
                <!-- uso sul bottone emit per creare un'evento custom  che chiamo search -->
                <button class="btn btn-primary" @click="$emit('search')">Search</button>
            </div>
        </form>
    </section>
</template>


<style lang="scss" scoped></style>