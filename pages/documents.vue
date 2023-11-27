<template>
  <header><NuxtLink to="/">Biuro Obsługi Studenta</NuxtLink></header>
  <main>
    <h1>WNIOSKI</h1>
    <div class="list" v-for="(user, index) in users" :key="index">
      <div class="list-element">
        <span>
          <div class="title">Wniosek o {{ user.title }}</div>
          <div class="info">
            {{ user.name }} {{ user.surname }} {{ user.album }}
          </div>
        </span>
        <div class="buttons">
          <NuxtLink to="/document-form"
            ><button title="Edytuj wniosek"><Icon name="fa-solid:pen" /></button
          ></NuxtLink>
          <button @click="deleteUser(index)" title="Usuń wniosek">
            <Icon name="fa-solid:trash-alt" />
          </button>
        </div>
      </div>
    </div>
    <NuxtLink to="/document-form"
      ><button class="create-btn" title="Dodaj nowy wniosek">
        <Icon name="fa-solid:plus" /></button
    ></NuxtLink>
  </main>
</template>
<script>
export default {
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    if (process.client) {
      this.users = JSON.parse(localStorage.getItem("users") || "[]");
    }
  },
  methods: {
    deleteUser(index) {
      this.users.splice(index, 1);
      localStorage.setItem("users", JSON.stringify(this.users));
    },
  },
};
</script>
