<template>
  <div class="single-album container">
    <NuxtLink class="btn-back" to="/"> Back </NuxtLink>
    <article class="single-album-details">
      <div class="single-album-cover">
        <img :src="`${album.cover}`" alt="" class="single-album-cover-img" />
        <img
          src="@/assets/images/376819.png"
          alt="single-album coverimg"
          class="single-album-cover-img"
          v-if="album.cover === ''"
        />
      </div>
      <div class="single-album-content">
        <p class="content-info">
          <span class="categorie">Artiste:</span> {{ album.artist }}
        </p>
        <p class="content-info">
          <span class="categorie">Nom:</span> {{ album.name }}
        </p>
        <p class="content-info">
          <span class="categorie">Sortie:</span> {{ album.year }}
        </p>
        <p class="content-info">
          <span class="categorie">Style:</span> {{ album.style }}
        </p>
        <p class="content-info">
          <span class="categorie">Format:</span> {{ album.format }}
        </p>
        <p class="content-info">
          <span class="categorie">Code barre:</span> {{ album.gencode }}
        </p>
      </div>
    </article>
    <button @click="deleteAlbum" class="btn-delete">Supprimer</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'album-details',
  data() {
    return {
      album: {},
    }
  },
  async fetch() {
    await this.getAlbum()
  },

  methods: {
    async deleteAlbum(e) {
      e.preventDefault()
      const data = axios.delete(
        `http://localhost:5000/album/${this.$route.params.id}`
      )
      const result = await data
      this.album = result.data
      console.log(result.data)
      redirect('/')
    },
    async getAlbum() {
      const data = axios.get(
        `http://localhost:5000/album/${this.$route.params.id}`
      )
      const result = await data
      this.album = result.data
      console.log(result.data)
    },
  },
}
</script>


<style lang="scss">
.btn-back {
  margin-left: 32px;
  margin-top: 32px;
  align-self: flex-start;
  margin-bottom: 32px;
  text-align: center;
  font-size: 16px;
  font-weight: bold;
  line-height: 30px;
  color: white;
  background-color: red;
  border: none;
  border-radius: 4px;
  text-decoration: none;
  padding: 6px 14px;
}
.btn-back:hover {
  background-color: rgb(138, 36, 36);
  transition: 0.3s;
}
.btn-delete {
  margin: auto;
  margin-bottom: 16px;
  margin-top: 16px;

  text-align: center;
  font-size: 16px;
  font-weight: bold;
  line-height: 30px;
  color: white;
  background-color: transparent;
  border: 1px solid red;

  border-radius: 4px;
  text-decoration: none;
  padding: 6px 14px;
}
.btn-delete:hover {
  background-color: rgb(138, 36, 36);
  transition: 0.3s;
}
.single-album {
  max-width: 1200px;
  height: 100%;
  display: flex;
  flex-direction: column;
  margin: auto;

  /* align-items: center; */

  .single-album-details {
    @media (max-width: 750px) {
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    display: flex;
    flex-direction: row;
    width: 100%;
    padding: 0 32px 32px 32px;
    height: 50%;
  }
}

.single-album-cover {
  display: flex;
  justify-content: center;
  align-items: center;
  /* width: 400px; */
  height: auto;
  &-img {
    max-height: 550px;
    width: auto;
  }
  @media (max-width: 750px) {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 400px;
    height: auto;
    &-img {
      padding-left: 32px;
      max-height: 720px;
      max-width: 100%;
    }
  }
}
.single-album-content {
  @media (max-width: 750px) {
    margin: auto;
  }
  margin: auto;

  color: white;
  font-size: 30px;
  .categorie {
    text-decoration: underline;
  }
  .content-info {
    padding: 5px 0 5px 0;
  }
}
</style>