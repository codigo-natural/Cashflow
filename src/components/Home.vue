<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume 
        :total-label="'ahorro total'"
        :label="label"
        :total-amount="10000"
        :amount="amount"
      >
        <template #graphic>
          <Graphic :amounts="amounts" />
        </template>
        <template #action>
          <Action @create="create" />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements 
        :movements="movements" 
        @remove="remove"
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
        movements: [
          {
            id: 1,
            title: "Movimiento",
            description: "Deposito de salario",
            amount: 1000,
            time: new Date("03-03-2024")
          },
          {
            id: 2,
            title: "Movimiento 1",
            description: "Deposito de honorarios",
            amount: 5000,
            time: new Date("03-03-2024")
          },
          {
            id: 3,
            title: "Movimiento 3",
            description: "Comida",
            amount: 3000,
            time: new Date("03-03-2024")
          },
          {
            id: 4,
            title: "Movimiento 4",
            description: "Colegiatura",
            amount: -1000,
            time: new Date("03-03-2024")
          },
          {
            id: 5,
            title: "Movimiento 5",
            description: "Reparación equipo",
            amount: 4000,
            time: new Date("03-03-2024")
          },
          {
            id: 6,
            title: "Movimiento 6",
            description: "Reparación equipo",
            amount: 2000,
            time: new Date("03-03-2024")
          },
          {
            id: 7,
            title: "Movimiento 7",
            description: "Reparación equipo",
            amount: -3000,
            time: new Date("04-04-2024")
          },
          {
            id: 8,
            title: "Movimiento 8",
            description: "Reparación equipo",
            amount: 6000,
            time: new Date("04-04-2024")
          },
          {
            id: 9,
            title: "Movimiento 9",
            description: "Reparación equipo",
            amount: -3000,
            time: new Date("04-04-2024")
          },
          {
            id: 10,
            title: "Movimiento 10",
            description: "Reparación equipo",
            amount: 1000,
            time: new Date("04-04-2024")
          },
          {
            id: 11,
            title: "Movimiento 11",
            description: "Reparación equipo",
            amount: -4000,
            time: new Date("04-04-2024")
          },
        ],
      };
    },
    computed: {
      amounts() {
        const lastDays = this.movements
          .filter(m => {
            const today = new Date();
            const oldDate = today.setDate(today.getDate() - 30);

            return m.time > oldDate;
          })
          .map(m => m.amount);

        return lastDays.map((m, i) => {
          const lastMovements = lastDays.slice(0, i)
          
          return lastMovements.reduce((suma, movement) => {
            return suma + movement
          }, 0)
        });
      }
    },
    methods: {
      create(movement) {
        this.movements.push(movement)
      },
      remove(id) {
        const index = this.movements.findIndex(m => m.id === id);
        this.movements.splice(index, 1)
      }
    }
  };
</script>
