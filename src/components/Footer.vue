<template>
  <div class="footer">
    &copy;{{ footer }} <a class="btn-info" :href="link">Jovane</a>
    {{ footer2 }} <a class="btn-info" :href="link2">Cod3r</a><br>
    Esquema de cores por minha irmã, Simone Cabral ★27.03.1973 †22.12.2020
  </div>
</template>

<script>
export default {
  data() {
    return {
      footer: "2020 - Lista de Tarefas Vue feita por ",
      footer2: ' a partir do Curso Vue JS 2 da ',
      link: 'https://jcgsr.github.io/',
      link2: 'https://www.udemy.com/course/vue-js-completo/'
    };
  }
};
</script>

<style scoped>
.footer {
  width: 100%;
  text-align: center;
  padding: 1rem;
  background: rgb(12, 1, 1);
  color: aliceblue;
}

a:link {
  text-decoration: none;
  color: yellow;
}

a:visited {
  color: yellow;
}
</style>
