<template>
  <div>
    <div v-if="this.bookables != null">
      <div class="row" v-for="row in rows" :key="'row' + row">
        <div
          class="col"
          v-for="(bookable, col) in bookables_in_row(row)"
          :key="'row' + row + col"
        >
          <bookable-list-item
            :title="bookable.title"
            :content="bookable.content"
            :price="bookable.price"
            :key="index"
          ></bookable-list-item>
        </div>

        <div class="col" v-for="(placeholder, idx) in placeholders_in_row(row)" :key="idx"></div>

      </div>
    </div>
  </div>
</template>

<script>
import BookableListItem from "./BookableListItem";
export default {
  components: {
    BookableListItem
  },
  computed: {
    rows() {
      return this.bookables == null
        ? 0
        : Math.ceil(this.bookables.length / this.columns);
    }
  },
  methods: {
    bookables_in_row(row){
      return this.bookables.slice((row - 1) * this.columns, row * this.columns);
    },
    placeholders_in_row(row){
      return this.columns - this.bookables_in_row(row).length;
    }
  },
  data() {
    return {
      columns: 3
    };
  },
  created() {
    this.bookables = [
      {
        title: "some title here",
        content: "some content here",
        price: 1000
      },
      {
        title: "some title here",
        content: "some content here",
        price: 1000
      },
      {
        title: "some title here",
        content: "some content here",
        price: 1000
      },
      {
        title: "some title here",
        content: "some content here",
        price: 1000
      },
      {
        title: "some title here",
        content: "some content here",
        price: 1000
      },
      {
        title: "some title here",
        content: "some content here",
        price: 1000
      },
      {
        title: "some title here",
        content: "some content here",
        price: 1000
      }
    ];
  }
};
</script>