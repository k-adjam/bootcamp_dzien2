<template>
    <div>
        <h1>Blog</h1>
        {{ wpisy }}
        <br/>
        <button @click="pobierzWpisy">Refresh</button>
        <input v-model="nowyBlog" type="text">
        <button @click="dodajWpisy">Add</button>
    </div>
</template>

<script>
import { dzien2_backend } from 'declarations/dzien2_backend/index';

export default {
    data() {
        return {
            wpisy: [],
            nowyBlog: ""
        }
    },
    methods: {
        async dodajWpisy() {
            await dzien2_backend.dodaj_wpis(this.nowyBlog);
        },
        async pobierzWpisy() {
            this.wpisy = await dzien2_backend.odczytaj_wpisy();
        }
    },

}
</script>