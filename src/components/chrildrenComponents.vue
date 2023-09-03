<template>
    <div class="hello">
        chrildrenComponents {{ count }}
    </div>
  </template>
  
  <script lang="ts">
    // import { setup } from "vue-class-component";
    import { ref, defineExpose } from "vue";

    export default {
        props:{
            person:() => {
                return {}
            }
        },
        setup(props: any, context: any) {
            console.log("chrildrenComponents props ==", props);
            console.log("chrildrenComponents context ==", context);
            const count = ref(10)


            type paramsType = {
                name:string,
                date:Date
            }
            function exportFunction(params:paramsType) {
                console.log("exportFunction", params);
                
            }
            defineExpose({exportFunction})
            console.log("props person ==", props.person);
            return {
                count,
                exportFunction
            }
        },
        mounted () {
            console.log("mounted person ==", this.person);
        }
    }

  </script>
  
  <style scoped>

  </style>
  