<script>
export default {
    data() {
        return {

        }
    },
    
    props: {
        rating: {
            type: Number,
            required: true
        }
    },

    computed: {
    stars() {
      return Math.round (this.rating/ 2)
    }
  }
}


</script>

<template>
    <div>
        <font-awesome-icon v-for="index in 5" :key="index" :icon="index <= stars ? 'star' : ['far', 'star']"
            class="star" />
    </div>
</template>

<style lang=scss scoped>
.star {
    color: gold;
}
</style>