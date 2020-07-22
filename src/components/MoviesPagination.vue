<template>
  <div class="movies-pagination d-flex justify-content-center">
    <b-pagination
      v-model="currentPageModel"
      :total-rows="total"
      :per-page="perPage"
      prev-text="Prev"
      next-text="Next"
    ></b-pagination>
    {{currentPage}}
  </div>
</template>

<script>
export default {
  name: "MoviesPagination",
  props: {
    perPage: {
      type: Number,
      default: 1
    },
    currentPage: {
      type: Number,
      default: 1
    },
    total: {
      type: Number,
      default: 1
    }
  },

  computed: {
    currentPageModel: {
      get() {
        return this.currentPage;
      },
      set(value) {
        this.$emit("pageChanged", value);
      }
    }
  }
};
</script>

<style scoped>
.movies-pagination {
  position: relative;
  z-index: 2;
  margin-top: 30px;
}
.movies-pagination >>> .pagination .page-item .page-link {
  background-color: transparent;
  font-size: 12px;
  color: #fff;
  box-shadow: none;
}

.movies-pagination >>> .pagination .page-item.active .page-link {
  border-color: #fff;
  background-color: #fff;
  color: #000;
}

.movies-pagination >>> .pagination .page-item.disabled .page-link {
  color: lightgrey;
}
</style>

