<template>
  <div class="welcome-page">
    <div class="title">
      <p>Biuro&nbsp;</p>
      <p>Obsługi&nbsp;</p>
      <p>Studenta</p>
    </div>
    <img
      src="https://www.torun.pl/sites/default/files/styles/node-image/public/field/image/wsb_merito_torun_logo_540.png?itok=XkHzyN19"
    />
  </div>
</template>
<script>
export default {
  mounted() {
    setTimeout(() => {
      this.$router.push("/documents");
    }, 3000);
  },
};
</script>
