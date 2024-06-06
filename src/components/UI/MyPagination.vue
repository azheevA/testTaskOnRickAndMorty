<template>
  <div class="page__wrapper">
    <div v-if="totalPages <= maxVisiblePages" v-for="pageNumber in totalPages" :key="pageNumber"
         class="page"
         :class="{ 'current-page': currentPage === pageNumber }"
         @click="handleChangePage(pageNumber)">
      {{ pageNumber }}
    </div>
    <div v-else class="page-container">
      <div class="page" :class="{ 'current-page': currentPage === 1 }" @click="handleChangePage(1)">1</div>
      <div v-if="startEllipsis" class="ellipsis">...</div>
      <div v-for="pageNumber in visiblePages" :key="pageNumber" class="page" :class="{ 'current-page': currentPage === pageNumber }" @click="handleChangePage(pageNumber)">
        {{ pageNumber }}
      </div>
      <div v-if="endEllipsis" class="ellipsis">...</div>
      <div class="page" :class="{ 'current-page': currentPage === totalPages }" @click="handleChangePage(totalPages)">{{ totalPages }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    totalPages: {
      type: Number,
      required: true,
    },
    currentPage: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      maxVisiblePages: 5,
    };
  },
  computed: {
    visiblePages() {
      const pages = [];
      const start = Math.max(2, this.currentPage - 2);
      const end = Math.min(this.totalPages - 1, this.currentPage + 2);
      for (let i = start; i <= end; i++) {
        pages.push(i);
      }
      return pages;
    },
    startEllipsis() {
      return this.currentPage > 3;
    },
    endEllipsis() {
      return this.currentPage < this.totalPages - 2;
    }
  },
  methods: {
    handleChangePage(pageNumber) {
      if (pageNumber !== this.currentPage) {
        this.$emit('page-changed', pageNumber);
      }
    },
  },
};
</script>

<style scoped>
.page__wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px 0;
}

.page-container {
  display: flex;
  align-items: center;
}

.page {
  margin: 0 5px;
  padding: 10px 15px;
  cursor: pointer;
  border: 1px solid #ddd;
  border-radius: 5px;
  background: linear-gradient(45deg, #6a0dad, #000);
  color: white;
  transition: background-color 0.3s, color 0.3s, transform 0.3s;
}

.page:hover {
  background-color: #e0e0e0;
  transform: scale(1.1);
}

.current-page {
  font-weight: bold;
  color: white;
  background: linear-gradient(45deg, #8a2be2, #000);
  border: 1px solid #8a2be2;
  animation: pulse 1s infinite;
}

@keyframes pulse {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.1);
  }
  100% {
    transform: scale(1);
  }
}

.ellipsis {
  padding: 10px 15px;
  color: #999;
}
</style>


