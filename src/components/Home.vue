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
          <Graphic :amounts="amounts" />
        </template>
        <template #action>
          <Action />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements 
        :movements="movements"
      />
    </template>
  </Layout>
</template>

<script>
  import Layout from "./Layout.vue"
  import Header from "./Header.vue"
  import Resume from "./Resume/index.vue"
  import Action from "./Action.vue"
  import Movements from "./Movements/index.vue"
  import Graphic from "./Resume/Graphic.vue"

  export default {
    components: {
      Layout,
      Header,
      Resume,
      Action,
      Movements,
      Graphic
    },
    data() {
      return {
        label: null,
        amount: null,
        amounts: [100, 200, 500, 200, -300, -600, 700, 0, 200, 500 -400],
        movements: [
        {
          id: 1,
          title: "Movimiento",
          description: "Deposito de salario",
          amount: "1000",
        },
        {
          id: 2,
          title: "Movimiento 1",
          description: "Deposito de honorarios",
          amount: "500",
        },
        {
          id: 3,
          title: "Movimiento 3",
          description: "Comida",
          amount: "-100",
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: "Colegiatura",
          amount: "1000",
        },
        {
          id: 5,
          title: "Movimiento 5",
          description: "Reparación equipo",
          amount: "1000",
        },
        {
          id: 6,
          title: "Movimiento 6",
          description: "Reparación equipo",
          amount: "1000",
        },
        {
          id: 7,
          title: "Movimiento 7",
          description: "Reparación equipo",
          amount: "10000",
        },
        {
          id: 8,
          title: "Movimiento 8",
          description: "Reparación equipo",
          amount: "1000",
        },
      ],
      }
    }
  }
</script>
