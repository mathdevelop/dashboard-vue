<template>
  <div id="home">
    <Header />
    <div id="welcome" class="row">
      <Card>
        <h2>Bem-vindo ao painel 360</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus accumsan tristique quam mattis pellentesque. Fusce ut leo sed orci vestibulum gravida. Interdum et malesuada fames ac ante ipsum primis in faucibus.</p>
      </Card>
    </div>
    <div class="row">
      <div class="w-60">
        <Card title="Temperatura na sua cidade">
          <Weather />
        </Card>
      </div>
      <div class="w-40">
        <Card title="Documentos favoritos">
          <Documents />
        </Card>
      </div>
    </div>
    <div class="row">
        <Card title="Galeria de fotos">
          <Gallery>
            <a href="#"><img src="@/assets/gallery/01.png"></a>
            <a href="#"><img src="@/assets/gallery/02.png"></a>
            <a href="#"><img src="@/assets/gallery/03.png"></a>
            <a href="#"><img src="@/assets/gallery/04.png"></a>
            <a href="#"><img src="@/assets/gallery/01.png"></a>
            <a href="#"><img src="@/assets/gallery/02.png"></a>
            <a href="#"><img src="@/assets/gallery/03.png"></a>
            <a href="#"><img src="@/assets/gallery/04.png"></a>
          </Gallery>
        </Card>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'
import Card from '@/components/Card.vue'
import Weather from '@/components/Weather.vue'
import Documents from '@/components/Documents.vue'
import Gallery from '@/components/Gallery.vue'

export default {
  name: 'Home',
  components: {
    Header,
    Card,
    Weather,
    Documents,
    Gallery
  }
}
</script>

<style scoped lang="scss">
#home {
  .row {
    display: flex;
    margin: 30px 0;
  }

  .w-60 {
    display: inline-block;
    width: calc(60% - 7.5px);
  }

  .w-40 {
    display: inline-block;
    width: calc(40% - 7.5px);
    margin-left: 15px;
  }

  #welcome {
    .card {
      display: flex;
      justify-content: center;
      flex-direction: column;
      min-height: 200px;

      h2 {
        margin: 0 0 15px;
        font-size: 27px;
        line-height: 32px;
        color: #000;
      }

      p {
        max-width: 785px;
        margin: 0;
        font-size: 16px;
        line-height: 19px;
        color: #393939;
      }
    }
  }
}
</style>
