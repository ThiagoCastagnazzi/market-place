<template>
  <div class="side-bar">
    <div class="side-bar__he ader">
      <div class="side-bar__header__title">
        <p><strong>Filtrar Por</strong></p>
      </div>
    </div>
    <div class="side-bar__content">
      <div class="side-bar__content__list">
        <div>
          <div class="side-bar__content__list__item__title">
            <button class="filterButton" @click="filterProducts('bag')">
              Bolsas
            </button>
            <button class="filterButton" @click="filterProducts('jacket')">
              Jaquetas
            </button>
            <button class="filterButton" @click="filterProducts('ssd')">
              SSD
            </button>
            <button class="filterButton" @click="filterProducts('ring')">
              Anéis
            </button>
            <button class="filterButton" @click="filterProducts('monitor')">
              Monitores
            </button>
            <button class="filterButton" @click="filterProducts('')">
              Sem Filtros
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    filterProducts(data) {
      this.$emit("filterProducts", data);
    },
  },
  name: "Sidebar",
};
</script>

<style scoped>
.side-bar {
  display: flex;
  flex-direction: column;
  max-width: 320px;
  height: max-content;
  padding: 10px;
  border: 1px solid #ccc;
}

strong {
  font-size: 20px;
  font-weight: bold;
}

.side-bar__content__list__item__title {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.filterButton {
  text-align: left;
  background: none;
  border: none;
  width: 100px;
  cursor: pointer;
}

.filterButton:hover {
  color: #42b983;
}
</style>
