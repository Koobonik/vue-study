<template>
  <div>
    <h1>Welcome to {{ title }}!</h1>
    <input type="text" v-model="input1" />
    <button type="button" @click="getData">Get</button>
    <button type="button" @click="setData">Set</button>
<!--    셀렉트 콤보 박스가 제주가 선택된 상태로 나올 것임    -->
    <select class="form-control" v-model="region" @change="changeRegion">
<!--      key에는 밸류값을, -->
      <option :key="i" :value="d.v" v-for="(d,i) in options">{{d.t}}</option>
    </select>
<!--    v-show 라는 옵션도 있음
v-show는 렌더링은 하지만 보여주지 않을뿐
v-if는 렌더링 할지말지
화면에 자주 보이고 안보이고 한다면 v-show를 써서 렌더링 횟수를 줄여주는게 좋음.-->
    <table class="table-bordered" v-if="tableShow">
      <!--  d => data, i => index    -->
      <tr :key="i" v-for="(d,i) in options">
        <td>{{d.v}}</td>
        <td>{{d.t}}</td>
      </tr>
    </table>
  </div>

</template>

<script>
import * as member from '@/api/member';

export default {
  data(){
    return {
      title:"pwmw의 품격",
      input1: "이런식으로!",
      tableShow: false,
      options: [
        {
          v:"S",
          t:"seoul"
        },
        {
          v:"J",
          t:"jeju"
        },
        {
          v:"B",
          t:"busan"
        }

      ],
      region: "J"
    };
  },
  methods:{
    getData(){
      alert(this.input1);
      member.getMembers().then(response => {
        console.log(response.data);
      }).catch(error => {
        console.log(error);
      });
    },
    setData(){
      this.input1 = "12345";
    },
    changeRegion(){
      alert(this.region)
    }

  },
  watch:{
    input1(){
      console.log(this.input1);
    }
  },
  beforeCreate() {
  },
  created() {
  },
  beforeMount() {
  },
  mounted() {
  },
  beforeUpdate() {
  },
  updated() {
  },
  beforeDestroy() {
  },
  destroyed() {
  }
}
</script>