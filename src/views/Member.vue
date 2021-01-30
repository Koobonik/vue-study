<template>
  <div id="member">
      <b-card :key="index" :value="member.memberID"  v-for="(member,index) in members"
              title="d.memberNickName"
              img-src="d.memberImageUrl"
              img-alt="Image"
              img-top
              tag="article"
              style="max-width: 20rem;"
              class="mb-2"
      >
        <b-card-text>
          Some quick example text to build on the card title and make up the bulk of the card's content.
        </b-card-text>

        <b-button href="#" variant="primary">Go somewhere</b-button>
      </b-card>

  </div>
</template>

<script>
import * as member from "@/api/member";
export default {
  name: "Member.vue",
  data(){
    return {
      members: []
    };
  },
  methods:{
    getData(){
      member.getMembers().then(response => {
        console.log(response.data);
        this.members.push(response.data);
        console.log(response.data.length);
        for(let i = 0; i < response.data.length; i++){
          this.members.push(JSON.stringify(response.data[i]));
          console.log(this.members)
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
#member{
  margin: 10px;
}
</style>