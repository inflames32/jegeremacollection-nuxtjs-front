<template>
  <div>
    <button @click="getPublicsAlbums">récupérer les albums</button>
    <div class="container">
      <article class="album" v-for="album in albumsPublics" :key="album._id">
        <div class="cover">
          <img
            src="@/assets/images/376819.png"
            alt=""
            class="cover"
            v-if="album.cover === ''"
          />
          <img :src="`${album.cover}`" alt="" class="cover" />
        </div>
        <p class="info">{{ album.artist }}</p>
        <p class="info">{{ album.format }}</p>
        <p class="info">{{ album.gencode }}</p>
        <p class="info">{{ album.name }}</p>
        <p class="info">{{ album.style }}</p>
        <p class="info">{{ album.year }}</p>
      </article>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      albumsPublics: [],
    }
  },
  /*  async fetch() {
    await this.getPublicsAlbums()
  }, */
  methods: {
    async getPublicsAlbums() {
      console.log('ici')
      const data = axios.get(
        /*     'https://mamediatheque-back.herokuapp.com/api/albums' */
        'http://localhost:5000/albums'
      )
      const result = await data

      result.data.forEach((album) => {
        this.albumsPublics.push(album)
      })

      console.log(this.albumsPublics)
    },
  },
}
</script>