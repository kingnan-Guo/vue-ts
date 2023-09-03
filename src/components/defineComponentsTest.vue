<template>
    <div class="defineComponentsTest">
        defineComponentsTest {{ count.data }}
    </div>
  </template>
  
  <script lang="ts">
    // import { setup } from "vue-class-component";
    import { ref, defineComponent, reactive } from "vue";

    const deC = defineComponent({
        setup() {
            const count = reactive({data:1})
            return {
                count
            }
        }
    })

    console.log("deC =", deC);
    
    export default deC

  </script>
  
  <style scoped>

  </style>
  