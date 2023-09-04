<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->
    {{msg}}
    <input v-model="Person.name"/>
    <button @click="submit">button</button>
    <chrildrenComponents ref="chrildrenComponentsRef" :person="Person" :getFatherList="getFatherList" />
    <defineComponentsTest></defineComponentsTest>
  </div>
</template>

<script lang="ts">
import { Options, setup, Vue } from 'vue-class-component';
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
import { computed, onMounted, reactive, Ref, ref } from "vue";
import chrildrenComponents from '@/components/chrildrenComponents.vue';
import defineComponentsTest from '@/components/defineComponentsTest.vue';

export default {
  components:{
    chrildrenComponents,
    defineComponentsTest
  },
  setup(props: any, context: any){
    console.log(" props ==", props);
    console.log(" context ==", context);
    
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


    const chrildrenComponentsRef = ref(null)
    
    onMounted(() => {
      
      console.log("chrildrenComponentsRef ==", chrildrenComponentsRef);
      let exportFunction = chrildrenComponentsRef.value?.['exportFunction']
      console.log("exportFunction ff =", exportFunction);
      
    })


    function getFatherList() {
      console.log("getFatherList");
      
    }

    return {
      msg,
      Person,
      chrildrenComponentsRef,
      getFatherList
    }
    
  },
  methods:{
    submit() {
      console.log("submit ==", this.Person);
      
    }
  }
}
</script>
