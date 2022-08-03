<template>
  <p>Edit the event here</p>
  <button @click="edit">Edit Me</button>
</template>

<script>
export default {
  props: ['id', 'event'], // Didn't add resa in 1.4
  inject: ['GStore'], // <--- Inject the Global Store
  methods: {
    edit() {
      // Assuming successful API call to register them

      // Set a flash message to appear on the next page loaded which says
      // 'You are successfully registered for ' + this.event.title

      this.GStore.flashMessage =
        'You successfully edited details for ' + this.event.title
      setTimeout(() => {
        // After 3 seconds remove it
        this.GStore.flashMessage = ''
      }, 3000)

      this.$router.push({
        name: 'EventDetails',
        params: { id: this.event.id }
      })
    }
  }
}
</script>
