<template>
  <div class='pt-12 d-flex flex-column align-center'>
    <v-btn @click="makeNewData">makeNewData</v-btn>
    <div class="mb-12">{{newKey}}</div>
    <div class='py-12'>
      ---------------구분선------------
    </div>
    <div class="d-flex pb-12">
      <v-btn @click="pushArr">pushArr</v-btn>
      <v-btn @click="objectAddFunc">객체 인덱싱 식추가</v-btn>
      <v-btn @click="setAddFunc">객체 set 인덱싱 식추가</v-btn>
      <v-btn @click="newAddFunc">객체 뉴배열 만들고 인덱싱 식추가</v-btn>
    </div>
    <div v-for="(value, index) in arr" :key="`${index}_${value}`">
      {{index}}번 순서 : {{value}}
    </div>
    <div class='py-12'>
      ---------------구분선------------
    </div>
    <div class="d-flex pb-12">
      <v-btn @click="addDeps1">dep1 레벌 일반 방식 추가</v-btn>
      <v-btn @click="addSetDeps1">dep1 레벌 set 추가</v-btn>
      <v-btn @click="changeDeps1Data">dep1 데이터 변경</v-btn>
    </div>
    <div v-for="(value, name, index) in dep1" :key="`${index}_${name}`">
      {{name}} : {{value}}
    </div>
    <div class='py-12'>
      ---------------구분선------------
    </div>
    <div class="d-flex pb-12">
      <v-btn @click="addDeps2">dep2 레벌 일반 방식 추가</v-btn>
      <v-btn @click="addSetDeps2">dep2 레벌 set 추가</v-btn>
      <v-btn @click="changeDeps2Data">dep2 데이터 변경</v-btn>
    </div>
    <div v-for="(value, name, index) in dep1.dep2" :key="`${index}_${name}`">
      {{name}} : {{value}}
    </div>
  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  data() {
    return {
      arr: [1, 2, 3, 4],
      newKey: '',
      dep1: {
        dep1Value: 'dep1의 값',
        dep2: {
          dep2Value: 'dep2의 값',
          dep3: {
            test: 1,
          },
        },
      },
    };
  },
  methods: {
    makeNewData() {
      this.newKey = '추가';
      console.log(this.newKey);
    },
    //
    pushArr() {
      this.arr.push(Math.random());
      console.log('addSetDeps1=>', this.arr);
    },
    objectAddFunc() {
      this.arr[this.arr.length] = Math.random();
      console.log(this.arr);
    },
    setAddFunc() {
      this.$set(this.arr, this.arr.length, Math.random());
      console.log('setAddFunc', this.arr);
    },
    newAddFunc() {
      const newArr = [...this.arr, Math.random()];

      this.arr = newArr;
      console.log('newAddFunc', this.arr);
    },
    //
    addDeps1() {
      this.dep1[Math.random()] = Math.random();
      console.log('addDeps1', this.dep1);
    },
    addSetDeps1() {
      this.$set(this.dep1, Math.random(), Math.random());
      console.log('addSetDeps1=>', this.dep1);
    },
    changeDeps1Data() {
      this.dep1.dep1Value = Math.random();
    },
    //
    addDeps2() {
      this.dep1.dep2[Math.random()] = Math.random();
      console.log('addDeps2', this.dep1.dep2);
    },
    addSetDeps2() {
      this.$set(this.dep1.dep2, Math.random(), Math.random());
      console.log('addSetDeps2=>', this.dep1.dep2);
    },
    changeDeps2Data() {
      this.dep1.dep2.dep2Value = Math.random();
    },
  },
};
</script>
