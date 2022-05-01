<template>
  <div class="homepage">
    <div>
      <div class="albums container">
        <div class="albums-grid" id="albums-grid">
          <article
            class="albums"
            v-for="(album, index) in albumsPublics"
            :key="index"
          >
            <div class="albums-cover">
              <img
                src="@/assets/images/376819.png"
                alt="album cover img"
                class="cover"
                v-if="album.cover === ''"
              />
              <img :src="`${album.cover}`" alt="" class="cover" />
            </div>
            <div class="informations">
              <p class="info">{{ album.artist }}</p>
              <p class="info">{{ album.name }}</p>
              <p class="info">
                {{ album.style.slice(0, 15) }}
                <span v-if="album.style.length > 15">...</span>
              </p>
              <p class="info">{{ album.year }}</p>
            </div>

            <NuxtLink
              class="details button"
              :to="{ name: 'album-albumid', params: { id: album._id } }"
            >
              Détails De L'album
            </NuxtLink>
          </article>
        </div>
      </div>
      <!--  <button class="addAlbum">
        <img src="@/assets/images/plus-svgrepo-com.svg" alt="" />
      </button> -->
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
  async fetch() {
    await this.getPublicsAlbums()
  },
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

<style lang="scss" scoped>
.homepage {
  .albums-grid {
    padding: 32px;
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
      grid-template-columns: repeat(4, 2fr);
    }
  }
  .albums {
    display: flex;
    flex-direction: column;
    position: relative;
    &-cover {
      position: relative;
      overflow: hidden;
      .cover {
        display: block;
        width: 100%;
        height: 100%;
      }
    }
  }

  .info {
    background-color: transparent;
    color: white;
    margin: 5px 0 5px 0;
  }
}
.details {
  text-align: center;
  font-size: 16px;
  font-weight: bold;
  line-height: 30px;
  color: white;
  background-color: #cc1414;
  border: none;
  border-radius: 4px;
  text-decoration: none;
  padding: 6px 14px;
}
.details:hover {
  background-color: rgb(138, 36, 36);
  transition: 0.5s;
}
.add-album {
  position: fixed;
  font-size: 50px;
  border-radius: 50px;
  bottom: 50px;
  right: 20px;
  width: 50px;
  height: 50px;
  border: none;
}
.add-album:hover {
  transform: rotate(360deg);
  transition: 0.5s;
}
</style>
