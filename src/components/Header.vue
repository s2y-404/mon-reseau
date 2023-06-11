<template>
  <header>
    <img src="@/assets/logo.png" alt="Logo" class="logo" />
    <h1 class="title">Mon réseau</h1>
    <div class="header-right">
      <div class="cube" style="width: 25px; height: 25px; display: block; background-color: #000;"></div>
      <h2 class="menu">Profil</h2>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderComponent',
  props: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header {
  width: 100%;
  height: 100px;

  display: flex;
  justify-content: space-between;
  text-align: center;
  align-items: center;
}

.header-right {
  display: flex;
  align-items: center;
}
.menu {
  padding-left: 25px;
}

.logo {
  width: 85px;
}
</style>
