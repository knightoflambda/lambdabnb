<template>
    <div>
        <bookable-list-item title="Villa 1" content="A really cheap Villa" :price="1000"></bookable-list-item>
        <bookable-list-item title="Villa 2" content="A really cheap Villa with two storeys" :price="2000"></bookable-list-item>
    </div>
</template>

<script>
import BookableListItem from "./BookableListItem"
export default {
    components: {
        BookableListItem
    }
}
</script>