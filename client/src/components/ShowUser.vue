<template>
  <div>
    <h1>ข้อมูล Steak</h1>
    <p>id: {{ userId }}</p>
    <p>ระดับความสุก {{ user.name }} - {{ user.lastname }}</p>
    <p>ช่องทางการติดต่อ email: {{ user.email }}</p>
    <p>ราคา: {{ user.password }}</p>
  </div>
</template>
<script>
import UserService from "@/services/UsersService";
export default {
  data() {
    return {
      user: null,
    };
  },
  async created() {
    try {
      let userId = this.$route.params.userId;
      this.user = (await UserService.show(userId)).data;
    } catch (error) {
      console.log(error);
    }
  },
};
</script>
<style scoped>
</style>