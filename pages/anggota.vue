<template>
    <div>
        <v-row v-if="isLoaded">
            <v-col cols="12" md="4" v-for="anggota in displayedAnggotas" :key="anggota.id">
                <v-card dark>
                    <div class="d-flex flex-no-wrap justify-space-between">
                        <div>
                            <v-card-title class="headline" v-html="anggota.name"></v-card-title>
                            <v-card-subtitle v-html="anggota.major.name"></v-card-subtitle>
                            <v-card-actions>
                                <v-btn :to="`/a/${anggota.id}`" text>View Profile</v-btn>
                            </v-card-actions>
                        </div>
                        <v-avatar
                            class="ma-3"
                            size="90"
                            tile
                            circle
                        >
                            <v-img :src="anggota.image_link"></v-img>
                        </v-avatar>
                    </div>
                </v-card>
            </v-col>
        </v-row>
        <div class="text-center">
            <v-pagination
            circle
            v-model="page"
            :length="pages.length"
            ></v-pagination>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    data() {
        return {
            anggotas: [],
            isLoaded: false,
            page: 1,
            perPage: 12,
            pages: [],
        }
    },
    methods: {
        async getDatas() {
            if(localStorage.z_anggotas) {
                this.anggotas = JSON.parse(localStorage.z_anggotas)
                this.isLoaded = true
            }
            await axios.get(`https://dev.imaka.or.id/api/anggota`)
            .then(res => {
                localStorage.z_anggotas = JSON.stringify(res.data.data)
                this.anggotas = res.data.data
                this.isLoaded = true
            })
        },
        setPages () {
            this.pages = []
            let numberOfPages = Math.ceil(this.anggotas.length / this.perPage)
            for (let index = 1; index <= numberOfPages; index++) {
                this.pages.push(index);
            }
        },
        paginate (posts) {
            let page = this.page;
            let perPage = this.perPage;
            let from = (page * perPage) - perPage;
            let to = (page * perPage);
            return  posts.slice(from, to);
        }
    },
    mounted() {
        this.getDatas()
    },
    watch: {
        anggotas () {
            this.setPages();
        }
    },
    computed: {
        displayedAnggotas () {
            return this.paginate(this.anggotas);
        }
    },
}
</script>