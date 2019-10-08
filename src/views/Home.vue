<template>
  <div class="home">
    <Selfbilling></Selfbilling>
  </div>
</template>

<script>
// @ is an alias to /src
import Selfbilling from '@/components/SelfBilling.vue'

export default {
  name: 'home',
  components: {
    Selfbilling
  }
}
</script>
