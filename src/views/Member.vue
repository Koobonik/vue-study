<template>
  <div id="member">
    <b-card :key="index" :value="member" v-for="(member,index) in members"
            v-bind:title="member.memberNickName"
            v-bind:img-src="member.memberImageUrl"
            img-alt="Image"
            img-top
            tag="article"
            style="max-width: 25rem; float:left; margin-right: 10px"
            class="mb-2"

    >
      <b-card-text>
        <strong>{{ member.sayOneThing }}</strong>
      </b-card-text>
      <h3><strong>기술 스택</strong></h3>
      <h4 :key="skill" :value="member" v-for="skill in member.skills">{{skill}}</h4>
      <b-button href="#" variant="primary">깃허브 보러가기</b-button>
    </b-card>

  </div>
</template>

<script>
import * as member from "@/api/member";

export default {
  name: "Member.vue",
  data() {
    return {
      members: []
    };
  },
  methods: {
    getData() {
      member.getMembers().then(response => {
        console.log(response.data);
        // this.members.push(response.data);
        console.log(response.data.length);
        for (let i = 0; i < response.data.length; i++) {
          this.members.push(response.data[i]);
          console.log(response.data[i]);
        }
        // this.members = response.data;
      }).catch(error => {
        console.log(error);
      });
    }
  },
  created() {
    this.getData();
  },
}

// eslint-disable-next-line no-unused-vars
class Member {

  constructor(memberID, memberNickName, sayOneThing, memberImageUrl, roles, skills) {
    this.memberID = memberID;
    this.memberNickName = memberNickName;
    this.sayOneThing = sayOneThing;
    this.memberImageUrl = memberImageUrl;
    this.roles = roles;
    this.skills = skills;
  }
}
</script>

<style scoped>
#member {
  margin: 10px;
}
</style>