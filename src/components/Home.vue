<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume 
        :label="label"
        :total-amount="100000"
        :amount="amount"
      >
      <template #graphic>
        graphic
      </template>
      <template #action>
        action
      </template>
      </Resume>
    </template>
    <template #movements>
      <Movements />
    </template>
  </Layout>
</template>

<script>
  import Layout from "./Layout.vue"
  import Header from "./Header.vue"
  import Resume from "./Resume/index.vue"
  import Movements from "./Movements.vue"

  export default {
    components: {
      Layout,
      Header,
      Resume,
      Movements,
    },
    data() {
      return {
        amount: null,
        label: 'Ahorro total',
      }
    }
  }
</script>