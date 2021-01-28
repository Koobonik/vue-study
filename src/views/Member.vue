<template>
  <div id="member">
    <div :key="i"  :v-for="(d,i) in members">
      <b-card
              title="Card Title"
              img-src="https://picsum.photos/600/300/?image=25"
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

  </div>
</template>

<script>
import * as member from "@/api/member";
export default {
  name: "Member.vue",
  data(){
    return {
      members: {
        
      }
    };
  },
  methods:{
    getData(){
      member.getMembers().then(response => {
        console.log(response.data);
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
</script>

<style scoped>
#member{
  margin: 10px;
}
</style>