<template>
<html>

<body>
    <div class="my-jumbotron" id="my-jumbotron">
      <nav class="navbar navbar-expand">
        <img src="/pictures/rueve-logo.svg" class="navbar-brand p-2"/>
        <ul class="navbar-nav">
        <li class="nav-item">
            <a class="nav-link" href="">Home</a>
        </li>
        <li class="nav-item">
            <a class="nav-link" href="">About</a>
        </li>
        <li class="nav-item">
            <a class="nav-link" href="">Shop</a>
        </li>
        </ul>
        <div class="collapse navbar-collapse">
          <ul class="nav navbar-nav ml-auto">
          <li class="nav-item mx-3  ">
              <a class="nav-link" href=""><img src="/pictures/user.svg" width="30px" height="30px"/></a>
          </li>
          <li class="nav-item mx-2">
              <a class="nav-link" href=""><img src="/pictures/shopping-cart.svg" width="30px" height="30px"/></a>
          </li>
          </ul>
        </div>
        </nav>
        <div class="container text-center" id="jumbo-text-contain">
            <h4 class="display-4 mt-5">Welcome To Rueve !</h4>
            <p class="lead">Belanja dengan mudah di Rueve</p>
            <button type="button" class="btn" id="jumbotron-btn">SHOP NOW !</button>
        </div>
    </div>
<div id="category-sect">
    <h4 class="font-weight-bold pt-5 text-center"> Shop By Category </h4>
      <section id="tabs" class="project-tab">
        <div class="container-fluid">
            <div class="row justify-content-center">
                <div class="col-md-12">
                    <b-tabs content-class="mt-3" fill>
                    <b-tab title="Shirts" active>
                    <ul class="container mt-4">
                          <div class="row">
                        <div v-for="(shirt, index) in shirts" :key="index" class="my-3 mr-2 text-center">
                          <div class="product-image">
                            <img :src="/pictures/ +pictshirt/+src" + index+src class="img-responsive h-75 w-100 p-2" />
                            </div>
                          <div class="product-details">
                            <h6 class="display-6 mt-3">{{ shirt.name }}</h6>
                            <h6 class="display-6 text-muted">Rp.{{ shirt.price }}</h6>
                          </div>
                        </div>
                    </div>
                    </ul>
                    </b-tab>
                    <b-tab title="T-Shirts">
                      <ul class="container mt-4">
                          <div class="row">
                        <div v-for="(tshirt, index) in tshirts" :key="index" class="my-3 mr-2 text-center">
                          <div class="product-image">
                            <img :src="pictures/tshirt/ + index +src" class="img-responsive h-75 w-100 p-2" />
                            </div>
                          <div class="product-details">
                            <h6 class="display-6 mt-3">{{ tshirt.name }}</h6>
                            <h6 class="display-6 text-muted">Rp.{{ tshirt.price }}</h6>
                          </div>
                        </div>
                    </div>
                    </ul>
                      </b-tab>
                    <b-tab title="Pants">
                      <ul class="container mt-4">
                          <div class="row">
                        <div v-for="(pant, index) in pants" :key="index" class="my-3 mr-2 text-center">
                          <div class="product-image">
                            <img :src="pictures/pants/ + index +src" class="img-responsive h-75 w-100 p-2" />
                            </div>
                          <div class="product-details">
                            <h6 class="display-6 mt-3">{{ pant.name }}</h6>
                            <h6 class="display-6 text-muted">Rp.{{ pant.price }}</h6>
                          </div>
                        </div>
                    </div>
                    </ul>
                    </b-tab>
                  </b-tabs>
                    </div>
                </div>
            </div>
            </section>
        </div>
</body>
<footer class="page-footer blue pt-5 mt-5">
<div class="container-fluid text-center text-md-left">
      <div class="row">
        <div class="col-md-6 mt-md-0 mt-3">
          <img class="px-5" src="/pictures/rueve-logo.svg" />
          <p class="text-md-left px-5">Sebagai Pusat Fashion Online di Asia, kami menciptakan kemungkinan-kemungkinan gaya tanpa batas dengan cara memperluas jangkauan produk, mulai dari produk internasional hingga produk lokal dambaan. Kami menjadikan Anda sebagai pusatnya. Bersama RUEVE, You Own Now.</p>

        </div>

        <hr class="clearfix w-100 d-md-none pb-3">
        <div class="col-md-3 mb-md-0 mb-3">

          <h5 class="text-uppercase">Layanan Kami</h5>

          <ul class="list-unstyled">
            <li>
              <a href="#!">Link 1</a>
            </li>
            <li>
              <a href="#!">Link 2</a>
            </li>
            <li>
              <a href="#!">Link 3</a>
            </li>
            <li>
              <a href="#!">Link 4</a>
            </li>
          </ul>

        </div>
        <div class="col-md-3 mb-md-0 mb-3">

          <h5 class="text-uppercase">TENTANG KAMi</h5>

          <ul class="list-unstyled">
            <li>
              <a href="#!">Link 1</a>
            </li>
            <li>
              <a href="#!">Link 2</a>
            </li>
            <li>
              <a href="#!">Link 3</a>
            </li>
            <li>
              <a href="#!">Link 4</a>
            </li>
          </ul>

        </div>

      </div>

    </div>

    <div class="footer-copyright text-right py-3 mr-3">© 2020 Copyright:
      <p> Rueve</p>
    </div>
  </footer>

</html>
</template>

<script>
import axios from 'axios'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
  name: 'App',
  data () {
    return {
      pictshirt: 'shirt',
      picttshirt: 'tshirt',
      pictpants: 'pants',
      src: '.jpg',
      tshirts: [],
      shirts: [],
      pants: []
    }
  },
  async created () {
    const baseURI = 'https://my-json-server.typicode.com/Wasomeno/myuts/db'
    axios.get(baseURI)
      .then((result) => {
        this.tshirts = result.data.tshirts
        this.shirts = result.data.shirts
        this.pants = result.data.pants
      })
  }
}

</script>

<style>

#my-jumbotron {
    background-size: cover;
    overflow: hidden;
}
#jumbo-text-contain {
    color: black;
    min-height: 400px;
}
#jumbotron-btn {
    font-size: 20px;
    border: 3px solid ;
    border-radius: 0;
    transition: 0.3s;
}
#jumbotron-btn:hover {
    color:white ;
    border: 1px solid white;
}
#products-container li{
    list-style-type: none;
    height: 250px;
}
.product-image {
    background: #f4f4ef;
    width: 250px;
    height: 275px;
}
.project-tab {
    padding: 10%;
    margin-top: -8%;
}
.project-tab #tabs{
    background: #007b5e;
    color: #eee;
}
.project-tab #tabs h6.section-title{
    color: #eee;
}
.project-tab #tabs .nav-tabs .nav-item.show .nav-link, .nav-tabs .nav-link.active {
    color: #20232a;
    background-color: transparent;
    border-color: transparent transparent #f3f3f3;
    border-bottom: 3px solid !important;
    font-size: 16px;
    font-weight: bold;
}
.project-tab .nav-link {
    border: 1px solid transparent;
    border-top-left-radius: .25rem;
    border-top-right-radius: .25rem;
    color: #acbebe;
    font-size: 16px;
    font-weight: 600;
}
.project-tab .nav-link:hover {
    border: none;
}
.project-tab thead{
    background: #f3f3f3;
    color: #333;
}
.project-tab a{
    text-decoration: none;
    color: #333;
    font-weight: 600;
}
.page-footer {
    color: white;
    background: #20232a;
}
</style>
