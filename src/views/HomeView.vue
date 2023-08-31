<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->
    {{msg}}
    <input v-model="Person.name"/>
    <button >button</button>
  </div>
</template>

<script lang="ts">
// import { Options, setup, Vue } from 'vue-class-component';
// import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

// @Options({
//   components: {
//     // HelloWorld,
//   },
// })
// export default class HomeView extends Vue {
//   public created() {
//     console.log('created');
      
//   }
//   public mounted() {
//     console.log('mounted');
//   }
//   public activated() {
//     console.log('activated');
//   }
// }
import { computed, reactive, Ref, ref } from "vue";
export default {
  setup(){
    const msg = ref('msg')
    const show:Ref<string> = ref('false')
    const Person = reactive({
        name: '123',
        parentName: 'koch',
        n: ''
    })
    // Person.n = computed(() => {
    //   return Person.name + Person.parentName
    // })
    console.log("Person =", Person);
    let asd:string
    asd = '234'
    console.log("asd =", asd);
    interface ArrListType {
      name:string,
      age: number
    }

    const arrList = ref<ArrListType[]>([])
    console.log("arrList= =", arrList);

    arrList.value = [{name: 'k', age: 3}]
    
    console.log("arrList= = 1 ", arrList);

    // Partial 是一个泛型类型，在使用时可以将任意类型作为参数传递给它，然后返回一个新的类型，该类型包含了原类型中的所有属性，但所有属性都变成了可选的
    type ObjListType = Partial<ArrListType>

    const objList = ref<ObjListType>({})
    objList.value = {name: 'g', age:45}
    console.log("objList  ", objList);

    return {
      msg,
      Person
    }
    
  },
  methods:{

  }
}


</script>
