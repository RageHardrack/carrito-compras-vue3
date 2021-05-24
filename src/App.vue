<template>
  <div class="container">
    <h1>Carrito</h1>
    <hr />
    <Carrito />
    <div class="row">
      <Card
        v-for="producto of productos"
        :key="producto.id"
        :producto="producto"
      />
    </div>
  </div>
</template>

<script>
import { useStore } from "vuex";
import { computed, onMounted } from "vue";
import Card from "@/components/Card.vue";
import Carrito from "@/components/Carrito.vue";

export default {
  name: "App",
  components: { Card, Carrito },
  setup() {
    const store = useStore();

    onMounted(() => {
      store.dispatch("fetchData");
    });

    const productos = computed(() => store.state.productos);
    // const carrito = computed(() => store.state.carrito);

    return { productos };
  },
};
</script>
