<template>
    <div v-if="this.bookable != null" class="row">
      <div class="col-md-8 pb-4">
        <div class="card">
          <div class="card-body">
            <h2>{{ bookable.title }}</h2>
            <hr/>
            <article> {{ bookable.description }} </article>
          </div>
        </div>
        <ReviewList :bookable-id="this.$route.params.id"></ReviewList>
      </div>
      <div class="col-md-4 pb-4">
          <Availability :bookable-id="this.$route.params.id"></Availability>
      </div>
    </div>
</template>

<script>
import Availability from "./Availability"
import ReviewList from "./ReviewList"

export default {
  components:{
    Availability,
    ReviewList
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
            this.bookable = response.data.data;
        });
  }
};
</script>