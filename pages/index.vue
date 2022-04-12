<template>
  <Tutorial />
</template>

<script>
import {storeToRefs} from "pinia"
import {useCounterStore} from "~/store/counter";
import {useStore} from "~/store/store";

export default {
  name: 'IndexPage',
  setup() {
    const counter = useCounterStore();

    counter.count++;
    counter.$patch({ count: counter.count + 1 });
    counter.increment();

    const store = useStore()
    const { name, doubleCount } = storeToRefs(store)
    const { increment } = store

    return {
      name,
      doubleCount,
      increment,
      store,
    }
  }
}
</script>
