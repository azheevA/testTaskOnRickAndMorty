<template>
  <div v-if="cards.length > 0" class="container">

    <transition-group name="card-list" >
      <card-item

          class="cards"
          v-for="(card) in cards"
          :card="card"
          :key="card.id"
      />

    </transition-group>
  </div>
  <h1 v-else >Не найдено</h1>
</template>

<script>
import CardItem from "@/components/CardItem.vue";

export default {
  components: {CardItem},
  props: {
    cards: {
      type: Array,
      required: true,
    }
  },
  methods: {

  },
  mounted() {

  },
}
</script>

<style scoped>
.container {
  left: 30px;
  right: 30px;
  position: absolute;
  font-size: 14px;
  border: 1px solid rgba(255,255,255,0.6);
  border-radius: 0.4rem;
  line-height: 20px;
  //overflow: hidden;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  align-items: center;
  flex-direction: column;
}
.cards{
  padding: 8px 0;
  align-items: center;
  justify-content: space-between;

}


.card-list-item {
  display: inline-block;
  margin-right: 10px;
}
.card-list-enter-active,
.card-list-leave-active {
  transition: all 0.4s ease;
}
.card-list-enter-from,
.card-list-leave-to {
  opacity: 0;
  transform: translateX(130px);
}
.card-list-move {
  transition: transform 0.5s ease;
}
h1 {
  align-items: center;
  justify-content: center;
  position: relative;
  top: 200px;
}
</style>
<!--createImage() {-->
<!--document.getElementById('img').setAttribute('src', this.card.image);-->
<!--}-->