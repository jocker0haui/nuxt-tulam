<template>
  <div>
    <CpnHeader />
    <Nuxt />
    <CpnFooter />
  </div>
</template>
<script>
import CpnHeader from '~/components/Header.vue'
import CpnFooter from '~/components/Footer.vue'
export default {
  name: 'DefaultLayout',
  components: {
    CpnHeader,
    CpnFooter,
  },
}
</script>
