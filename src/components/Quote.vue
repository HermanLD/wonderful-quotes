<template>
  <div class="card text-center m-2 clickable" @click="removed">
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    index: Number
  },
  methods: {
    removed() {
      this.$emit("removedQuote", this.index);
    }
  }
};
</script>

<style scoped>
.clickable {
  font-family: "Pacifico", cursive;
  font-size: 28px;
  height: 200px;
}

.clickable:hover {
  cursor: pointer;
}
</style>
