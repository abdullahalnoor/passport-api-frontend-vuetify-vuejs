<template>
   <v-container fluid fill-height>
        <v-layout align-center justify-center>
         
        </v-layout>
      </v-container>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
<script>
export default {
  created() {
    localStorage.removeItem("token");
  }
};
</script>
