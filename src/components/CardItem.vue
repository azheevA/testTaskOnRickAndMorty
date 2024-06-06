<template>
  <div class="card" @mouseover="toggleInfo(true)" @mouseleave="toggleInfo(false)">
    <img id="img" :src="card.image" alt="image is not found" />
    <div class="first" :class="{ 'hidden': showInfo }">{{card.name}}</div>
    <div class="card-content">
      <div class="info">
        <strong>Имя: </strong>{{card.name}} <br>
        <strong>Статус: </strong>{{card.status}} <br>
        <strong>Раса: </strong>{{card.species}} <br>
        <strong>Гендер: </strong>{{card.gender}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    card: {
      type: Object,
      required: true,
    }
  },
  data() {
    return {
      showInfo: false
    };
  },
  methods: {
    toggleInfo(value) {
      this.showInfo = value;
    }
  }
}
</script>

<style scoped>
.card {
  color: turquoise;
  background-color: #1e0707;
  max-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  font-size: 16px;
  font-family: 'Arial', sans-serif;
  border: 3px solid rgba(255, 255, 255, 0.6);
  border-radius: 0.8rem;
  width: 285px;
  height: 360px;
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  margin: 30px;
  position: relative;
}

.card:hover {
  transform: scale(1.1);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

.first {
  width: 100%;
  position: absolute;
  bottom: 15px;
  left: 0;
  color: #ffcc00; /* Новый цвет текста */
  font-size: 22px; /* Увеличенный размер текста */
  font-family: 'Courier New', Courier, monospace; /* Новый шрифт */
  padding: 10px 10px;
  transition: opacity 0.5s ease;
  background-color: rgba(30, 7, 7, 0.8);
  text-align: center;
}

.hidden {
  opacity: 0;
}

.card-content {
  width: 100%;
  position: absolute;
  bottom: 0;
  left: 0;
  padding: 10px;
  background-image: linear-gradient(180deg, #000000, #1e0707);
  transition: opacity 0.5s ease;
  opacity: 0;
}

.card:hover .card-content {
  cursor: pointer;
  opacity: 1;
}

.info {
  opacity: 0;
  transition: opacity 0.3s ease;
  padding: 20px;
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(22, 22, 22, 0.9);
  background-image: radial-gradient(#1e0707, #000000);
  border-radius: 0.8rem 0.8rem 0 0;
  transform: translateY(100%);
  color: #ffffff;
  font-weight: bold;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  z-index: 1;
}

.card:hover .info {
  opacity: 1;
  transform: translateY(0);
}
</style>