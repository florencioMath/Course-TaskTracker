<template>
  <div class="wrapper">
    <h3>Sobre</h3>
    <br />
    <p>
      App criado para iniciar os estudo em VueJS. <br />
      Seguindo esse Crash Course:
      <a
        href="https://www.youtube.com/watch?v=qZXt1Aom3Cs&ab_channel=TraversyMedia"
        target="_blank"
        >Vue JS Crash Course</a
      >.
    </p>
    <br />
    <RouterLink to="/">Voltar para Tasks</RouterLink>
  </div>
</template>

<script>
import { RouterLink } from 'vue-router';

export default {
  name: 'About',
  components: { RouterLink },
};
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  flex-direction: column;
  margin-top: 30px;
}
</style>
