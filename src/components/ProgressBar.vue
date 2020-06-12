<template>
  <div class="col">
    <h4 class="text-white">Quotes Added</h4>
    <div class="progress">
      <div
        class="progress-bar progress-bar-striped progress-bar-animated"
        role="progressbar"
        :style="{ width: progressPc + '%' }"
        :aria-valuenow="{ progressPc }"
        aria-valuemin="0"
        aria-valuemax="10"
      >
        {{ quoteStorage }} / 10
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    quoteStorage: Number
  },
  computed: {
    progressPc() {
      return this.quoteStorage * 10;
    }
  }
};
</script>
