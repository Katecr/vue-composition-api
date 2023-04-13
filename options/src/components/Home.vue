<template>
  <div>{{ counter }}</div>
</template>

<script>
    import { reactive, watch, ref } from "vue";
    
    export default {
        setup() {
            const obj = reactive({counter:0});
            const counter = ref(0);

            setInterval(() => obj.counter++,500);
            setInterval(() => counter.value++,500);

            // watch( () => obj.counter, (value, old) => {
            //     console.log(value, old);
            // });
            
            watch(counter, (value, old) => {
                console.log(value, old);
            });
            return { 
              counter,
            }
        },
    };
</script>