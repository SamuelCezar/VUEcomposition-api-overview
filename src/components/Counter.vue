<template>
  <p>Initial value: {{ initialValue }}</p>
  <p>Actual value: {{ count }}</p>
  <p>Triple value: {{ triple }}</p>
  <button @click="add">Add</button>
</template>

<script>
import { ref, computed, watch, onMounted } from "vue";
export default {
  // eslint-disable-next-line
  name: "Counter",
  props: {
    initialValue: Number,
  },
  setup(props) {
    console.log(props);

    const count = ref(props.initialValue);
    const triple = computed(() => count.value * 3);

    const add = () => {
      count.value++;
    };

    watch(count, (newValue, oldValue) => {
      console.log("Old value: " + oldValue + " New value: " + newValue);
    });

    onMounted(()=>{
      console.log("On mounted")
    })

    return { count, add, triple };
  },
};
</script>

<style scoped>
</style>
