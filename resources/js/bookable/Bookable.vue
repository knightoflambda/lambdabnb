<template>
  <div>
    <div v-if="this.bookable != null">
      <div class="row mb-4">
        <div class="col d-flex align-items-stretch">
          <bookable-list-item
            :title="bookable.title"
            :description="bookable.description"
            :price="bookable.price"
            :key="bookable.id"
          ></bookable-list-item>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BookableListItem from "../bookables/BookableListItem";

export default {
  components: {
    BookableListItem  
  },
  data() {
    return {
      bookable: null,
      id: null
    };
  },
  created(){
      this.id = this.$route.params.id;
      const request = axios
        .get(`/api/bookables/${this.id}`)
        .then(response => {
            this.bookable = response.data;
        });
  }
};
</script>