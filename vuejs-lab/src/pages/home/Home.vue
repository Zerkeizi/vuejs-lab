<template>

  <div class="module__wrapper">
    <h1 class="title">{{ title }}</h1>  

    <input class="filter" type="search" @input="filter = $event.target.value" placeholder="Pesquise">
    <ul class="picture__wrapper">
      <li v-for="picture of filteredGallery">

      <Frame :title="picture.titulo">
        <Picture :url="picture.url" :titulo="picture.titulo"/>
      </Frame>

     </li>
    </ul>

  </div>
</template>


<script>
  import Frame from '../../components/gallery/Frame';
  import Picture from '../../components/picture/Picture';
  export default {
    components: {
      Frame: Frame,
      Picture: Picture
    },
  
    data () {
      return {
        title: 'Gallery',
        pictures: [],
        filter: '',
      }
    },
    computed: {
      filteredGallery() {
        if (this.filter) {
          let exp = new RegExp(this.filter.trim(), 'i');
          return this.pictures.filter(pic => exp.test(pic.titulo))
        } else {
          return this.pictures;
        }
      }
    },
    created() {

      this.$http.get('http://localhost:3000/v1/fotos')
        .then(res => res.json())
        .then(fotos => this.pictures = fotos, err => console.log(err));
        // .then(res => console.log(res))

    }
  }
</script>

<style lang="scss">
.module__wrapper {
    font-family: Helvetica, sans-serif;

    .filter {
      margin: 0px auto;
      display: block;
      margin-bottom: 40px;
      padding: 10px 10px;
      width: 100%;
      max-width: 675px;
    }
    
    .title {
      text-align: center;
    }

    .picture__wrapper {
          display: grid;
          grid-template-columns: 1fr 1fr 1fr;
          grid-gap: 20px;
          padding: 0px;
          max-width: max-content;
          margin: 0px auto;

      li {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: blue;
        border: 1px solid;
        padding: 10px 30px;
        max-width: 150px;
      }
    }
  }
</style>
