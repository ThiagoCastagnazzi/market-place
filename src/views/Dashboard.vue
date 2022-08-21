<template>
  <div>
    <h1>Dashboard</h1>
    <div class="sidebar">
      <b-button v-b-toggle.collapse-2 class="m-1">Toggle Collapse</b-button>

      <b-collapse id="collapse-2">
        <b-card>Produtos</b-card>
        <b-card>Usuarios</b-card>
      </b-collapse>
    </div>
    <div>
      <div>
        <h2>Produtos Cadastrados</h2>
      </div>
      <div>
        <h2>Usuarios Cadastrados</h2>
      </div>
    </div>
  </div>
</template>

<style>
.container-dashboard {
  display: flex;
  flex-direction: column;
  border: 1px solid #ccc;
}

.sidebar {
  position: absolute;
}
</style>
