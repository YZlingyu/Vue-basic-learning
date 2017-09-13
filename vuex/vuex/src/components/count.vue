<template>
  <div>
    <h2>{{msg}}</h2>
    <hr/>
    <h3>{{$store.state.count}}-{{count}}</h3>
    <p>
      <!--commit()是固定写法-->
      <button @click="$store.commit('add',10)">+</button>
      <button @click="reduce">-</button>
    </p>

    <p>
      <!--commit()是固定写法-->
      <button @click="addAction">+</button>
      <button @click="reduceAction">-</button>
    </p>

  </div>
</template>

<script>
  import store from '@/vuex/store';
  //第二种方法：mapState
  import {mapState,mapMutations,mapGetters,mapActions } from 'vuex';

  export default {
    data(){
      return{
        msg:`hello vuex`
      }
    },
    //赋值三种方法，1。计算属性
   /* computed: {
      count() {
        return this.$store.state.count;
      }
    },*/
   //2. mapState
    /*computed:mapState({
      count: state => state.count
    }),*/
    //3.利用数组实现
    computed:{
      ...mapState(['count']),
      /*count(){
        return this.$store.getters.count;
      }*/
      //...mapGetters(["count"])
    },
    methods:{
      ...mapMutations(['add','reduce']),
      ...mapActions(['addAction','reduceAction'])
    },
    store
  }
</script>

<style>
</style>
