<template>
  <div class="home">
    <div class="container">
      <b-overlay :show="show" rounded="sm">
        <h1 class="title">Produtos</h1>
        <div class="search-container">
          <div>
            <p class="search-text" v-if="filter">Search for {{ filter }}</p>
            <p class="search-text" v-else>All Products</p>
          </div>
          <b-form-input v-model="filter" placeholder="Search..."></b-form-input>
        </div>

        <div class="products-container">
          <Sidebar
            @filterProducts="filterProducts($event)"
            @filterJacket="filterJacket($event)"
          />
          <div class="card-container-grid">
            <div v-for="(product, index) in produtoFiltrado" :key="index">
              <b-card>
                <div>
                  <img
                    class="product-img"
                    :src="product.image"
                    :alt="product.title"
                  />
                </div>
                <div>
                  <p class="card-text">
                    {{ product.title }}
                  </p>
                </div>
              </b-card>
            </div>
          </div>
        </div>
      </b-overlay>
    </div>
  </div>
</template>

<script>
import Sidebar from "@/components/Sidebar.vue";

export default {
  data() {
    return {
      show: false,
      products: [],
      filter: "",
    };
  },
  components: {
    Sidebar,
  },
  methods: {
    getProducts() {
      this.show = true;
      fetch("https://fakestoreapi.com/products")
        .then((r) => r.json())
        .then((data) => {
          this.products = data;
          this.show = false;
        });
    },

    filterProducts(data) {
      this.filter = data;
    },
  },

  computed: {
    produtoFiltrado() {
      if (!this.filter) return this.products;
      return this.products.filter((product) => {
        return product.title.toLowerCase().includes(this.filter);
      });
    },
  },

  mounted() {
    this.getProducts();
  },
};
</script>

<style scoped>
.title {
  padding: 10px 0;
}

.products-container {
  display: grid;
  grid-template-columns: 2fr 7fr;
  gap: 2rem;
}

.card-container-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
}

.card {
  display: flex;
  flex-direction: column;
}

.card-body {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  gap: 5px;
}
.product-img {
  width: 200px;
  height: 200px;
  object-fit: contain;
}

.card-text {
  font-size: 0.875rem;
  line-height: 1.125rem;
  font-weight: 600;
  margin-top: 0.5rem;
  overflow: hidden;
  text-overflow: ellipsis;
  height: 3.375rem;
}

.search-container {
  display: flex;
  justify-content: space-between;
  padding: 20px 0;
}

.form-control {
  width: 50ch;
}

.search-text {
  font-size: 1.3rem;
  font-weight: bold;
  text-transform: capitalize;
}

@media screen and (max-width: 500px) {
  .search-container {
    flex-direction: column;
  }
  .form-control {
    width: 100%;
  }
}
</style>
