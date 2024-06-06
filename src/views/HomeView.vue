<template>
  <div class="home">
    <h1>Список персонажей</h1>
    <div class="header">
      <my-input
          v-model="searchQuery"
          placeholder="Поиск ..."
          class="input"
      />
      <my-select
          v-model="selectedSort"
          :options="sortOptions"
          class="select"
      />
    </div>

    <card-list
        v-bind:cards="sortedAndSearchedCards"
        class="list"
    />
    <!--    <MyPagination  :totalPages="info.pages" :currentPage.sync="page" >-->
    <!--    {{page}}-->
    <!--    </MyPagination>-->
    <my-pagination :total-pages="totalPages" :current-page="currentPage" @page-changed="fetchCards" />
  </div>

</template>

<script>
// @ is an alias to /src
import { ref } from 'vue';

import axios from "axios";
import CardList from "@/components/CardList.vue";
import MySelect from "@/components/UI/MySelect.vue";
import MyInput from "@/components/UI/MyInput.vue";
import MyPagination from "@/components/UI/MyPagination.vue";

export default {
  name: 'HomeView',
  components: {
    MyPagination,
    MyInput,
    MySelect,
    CardList,

  },
  data(){
    return{
      selectedSort: '',
      searchQuery: '',
      cards: [],
      currentPage: 1,
      totalPages: 10,
      // isCardLoading: false,
      loading: true,
      info: {
        count: 826,
        pages: 1,
      },
      sortOptions: [
        {value: 'name', name: 'По имени'},
        {value: 'status', name: 'По статусу'},
      ],

    }
  },
  methods: {
    changePage(Number){
      this.page=pageNumber;
      this.fetchCards();
    },
    fetchCards(pageNumber){
      this.currentPage=pageNumber;
      fetch(`https://rickandmortyapi.com/api/character/?page=${pageNumber}`)
          .then(response => response.json())
          .then(data => {

            this.loading = false;
            this.cards = data.results;
            this.totalPages=data.info.pages;
            // this.info=Object.assign(({},this.info, {pages: data.info.pages}));
            // vm.$set(this.info, 'pages', data.info.pages)
            //this.$set(this.info, 'pages', data.info.pages)
          });


    },



  },
  mounted() {

    this.fetchCards(this.currentPage);
  },
  computed: {
    sortedCards(){
      return [...this.cards].sort((card1,card2) =>
          card1[this.selectedSort]?.localeCompare(card2[this.selectedSort])
      );
    },
    sortedAndSearchedCards(){
      return this.sortedCards.filter(card => card.name.includes(this.searchQuery))
    }
  }
}
console.log();
</script>

<style>
.home{
  overflow-y: hidden;
}
.header {
  margin: auto;
  top: 330px; /* Измените это значение на ваше усмотрение */
  right: 0;
  position: absolute;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center; /* Центровка по вертикали */
  z-index: 3;
  max-width: 480px; /* Установите желаемую максимальную ширину */
}

.input {
  margin-right: 5px; /* Отступ справа */
}

.select {
  margin-left: 5px; /* Отступ слева */
  font-size: 15px;
  position: relative;
}

.select::before {
  content: '';
  position: absolute;
  top: 50%;
  height: 40px; /* Высота линии */
  width: 1px; /* Ширина линии */
  background-color: #fff; /* Цвет линии */
  left: 6px;
  transform: translateY(-50%);
}


.list {
  position: absolute;
  top: 380px;
  margin-top: 30px;
  align-self: center;
}

h1 {
  margin: 0 auto;
  position: absolute;
  left: 0;
  right: 0;
  top: 100px;
  justify-content: center;
  font-size: 45px;
  color: #149387;
}



</style>
<!-- async fetchCards(){
      try{
        const response = await axios.get(`https://rickandmortyapi.com/api/character`)
            // .then(response => console.log("response", response.data));
        // this.totalPages =
        //     Math.ceil(response.data.info.page);

        this.cards = response.data;
        console.log(response.data);
        console.log(this.cards)
      }catch (e){
        alert('Error')
      }finally {
        this.isCardLoading = false;
      }
    },-->
<!--
<div class="page__wrapper">
<div v-for="pageNumber in info.pages"
     :key="pageNumber"
     class="page"
     :class="{
             'current-page': page === pageNumber
           }"
     @click="changePage(pageNumber)"
>
  {{pageNumber}}
</div>
</div>

.page__wrapper {
  display: flex;
  position: relative;
  margin: 0;
  cursor: pointer;
}

.page {
  margin: 3px;
  border: 1px solid turquoise;
  background-color: #42b983;
  color: #2c3e50;
  border-radius: 3px;
}

.current-page {
  scale: 1.2;
}
-->