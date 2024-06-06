<template>
  <div class="about">
    <h1>Тут расписано реализация проекта</h1>
    <div>

      <p>
        <u>Заранее извинияюсь, что текст написан в довольно просторечивом ключе.</u>
        <br>
        <br>
        <strong>1. Проблематика.</strong> Проект написан на фреймворке vue3. Разработка имела для меня <br>
        много подводных камней при реализации проекта. Во первых, путаница в свойствах в option api,<br>
        к примеру, не понимал смысл свойства watch, были проблемы с реактивностью <br>
        во vue(ref, reactive и computed), с некоторыми директивами, не понимание $emit (при передачи данных в родительский компонент) и т.д.<br>
        К тому же, переход на composition api в UI компонентах, реализующих пагинацию и фильтрацию, и их взаимодействие с родительским компонентом<br>
        <br>
        <strong>2. Дополнение.</strong>  Описание
        Также при написании я изучал централизованное хранилище vuex, которое в будущем я хочу реализовать ради опыта.<br>
        <strong>3. Реализация.</strong> Как вы уже видите, в программе настроен роутинг, который ссылается на два компонента, <br>
        где первый компонент - это сам проект, а второй - это мое описание об реализации и соответствующие мысли об данном проекте.<br>
        Для выполнения HTTP-запроса я обратился к помощи fetch api, также имеются знания библиотеки axios. Пагинацию реализовал со скрытием,
        которое для меня ново. Компонент CardList и дочерний ему элемент CardItem, очевидно выполняют роль визуального вывода данных.<br>

      </p>
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