<template>
    <div class="hello">
        chrildrenComponents {{ count }}

        <button @click="clickFatherFUnction">clickFatherFUnction</button>
    </div>
  </template>
  
  <script lang="ts">
    // import { setup } from "vue-class-component";
    import { ref, defineExpose, defineProps } from "vue";
    // const props = defineProps({
    //     getFatherList: {
    //         type: Function,
    //         default: Function,
    //         required: true
    //     }
    // })

    export default {
        props:{
            person:() => {
                return {}
            },
            getFatherList: {
                type: Function,
                default: Function,
                required: true
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
            
            function clickFatherFUnction() {
                console.log("clickFatherFUnction");
                props.getFatherList()
                
            }
            
            
            return {
                count,
                exportFunction,
                clickFatherFUnction
            }
        },
        mounted () {
            console.log("mounted person ==", this.person);
        }
    }

  </script>
  
  <style scoped>

  </style>
  