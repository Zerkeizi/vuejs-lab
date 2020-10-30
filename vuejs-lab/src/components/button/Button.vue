<template>
  <button 
    @click="action"
    class="button"
    :type="type"
  >
    {{ label }}
  </button>
</template>
<script>
export default {
  props: {
    type: String,
    label: String,
    confirmation: Boolean,
  },
  methods: {
    action() {
      console.log(typeof this.confirmation)
      if (this.confirmation) {
        if (confirm('Você tem certeza?')) {
          this.$emit('buttonCustomClick')
        }
      } else {
        this.$emit('buttonCustomClick')
      }
    }
  }
};
</script>
<style lang="scss" scoped>
.button {
  border-radius: 6px;
  padding: 10px 20px;
  border: none;
  text-transform: uppercase;
  font: normal 600 16px/1.5em "Montserrat", sans-serif;
  cursor: pointer;
  color: #fff;
  transition: all .3s;

  &--primary {
    background-color: #33b3c3;

    &:hover {
      background-color: #227b86;
    }
  }

  &--danger {
    background-color: firebrick;
  }
}
</style>