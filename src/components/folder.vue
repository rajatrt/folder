<template>
  <div>
    <div :style="`margin-left: ${depth * 50}px`" @click="toggleChildren" class="heading">
      <i class="fas fa-caret-down" v-if="showChildren"></i>
      <i class="fas fa-caret-right" v-else></i>
      <i class="far fa-folder"></i>
      {{ index }}
    </div>
    <div v-if="recursiveCall">
      <folder 
        v-show="showChildren"
        v-for="(f,index) in fold" 
        :key="f"
        :fold="f"
        :index="index"
        :depth="depth+1"/>
    </div>
    <div v-else-if="showChildren">
       <div v-for="f in fold" :key="f" :style="`margin-left: ${depth * 50 +20}px`">{{ f }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'folder',
  props: {
    fold:{

    },
    index:{
      type: String,
    },
    depth:{
      type: Number
    }
  },
  data(){
    return {
      recursiveCall: false,
      showChildren: false
    }
  },
  methods:{
    toggleChildren(){
      this.showChildren = !this.showChildren;
    }
  },
  mounted(){
    if(Array.isArray(this.fold)){
      this.recursiveCall = false;
    } else {
      this.recursiveCall = true;
    }
  }
}
</script>

<style scoped>
.fas,.far{
  margin: 0 .2rem;
}
.heading{
  cursor: pointer;
}
</style>
