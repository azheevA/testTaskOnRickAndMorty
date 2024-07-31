<template>
  <div class="about">
    <h1>Тут расписано реализация проекта</h1>
    <div>

    </div>
  </div>
</template>

<script setup>
import CardList from "@/components/CardList.vue";
</script>

<style scoped>
.about {

  color: #999;
  padding: 20px;
  border-radius: 10px;
  max-width: 800px;
  margin: 40px auto;
  line-height: 1.6;
  font-family: 'Georgia', serif;
  text-align: justify;
}

h1 {
  font-size: 2em;
  margin-bottom: 20px;
  text-align: center;
}

div p {
  position: relative;
  top: 200px;
  font-size: 1.2em;
  line-height: 1.6;
  margin: 20px 0;
}

strong {
  font-size: 1.3em;
  display: block;
  margin-top: 20px;
}

</style>
