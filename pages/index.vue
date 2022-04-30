<template>
  <div class="homepage">
    <Header />

    <div>
      <button @click="getPublicsAlbums" v-if="albumsPublics !== []">
        Récupérer les albums
      </button>
      <div class="container albums">
        <div class="albums-grid" id="albums-grid">
          <article
            class="album"
            v-for="(album, index) in albumsPublics"
            :key="index"
          >
            <div class="album-cover">
              <img
                src="@/assets/images/376819.png"
                alt="album cover img"
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

<style scoped>
.homepage {
  .albums-grid {
    display: grid;
    column-gap: 32px;
    row-gap: 64px;
    grid-template-columns: 1fr;
    @media (min-width: 500px) {
      grid-template-columns: repeat(2, 1fr);
    }
    @media (min-width: 750px) {
      grid-template-columns: repeat(3, 1fr);
    }
    @media (min-width: 1100px) {
      grid-template-columns: repeat(4, 1fr);
    }
  }
  .album {
    display: flex;
    flex-direction: column;
    position: relative;
  }
  .album-cover {
    position: relative;
    overflow: hidden;
  }
  .cover {
    display: block;
    width: 100%;
    height: 100%;
  }
}
</style>
