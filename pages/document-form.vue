<template>
  <header><NuxtLink to="/">Biuro Obsługi Studenta</NuxtLink></header>
  <main>
    <h1>TRYB EDYCJI</h1>
    <form @submit.prevent="storeData" class="formularz">
      <div>
        <input
          class="text-input"
          type="text"
          id="title"
          v-model="title"
          required
          placeholder="TYTUŁ"
        />
      </div>
      <div>
        <input
          class="text-input"
          type="text"
          id="name"
          v-model="name"
          required
          placeholder="IMIĘ"
        />
      </div>
      <div>
        <input
          class="text-input"
          type="text"
          id="surname"
          v-model="surname"
          required
          placeholder="NAZWISKO"
        />
      </div>
      <div>
        <input
          class="text-input"
          type="text"
          id="album"
          v-model="album"
          required
          placeholder="NR ALBUMU"
        />
      </div>
      <div>
        <label for="file" class="custom-file-upload"> ZAŁĄCZ PLIK </label>
        <input type="file" id="file" @change="handleFileChange" />
      </div>
      <div class="buttons">
        <button type="submit" @click="submitForm">
          <Icon name="fa6-solid:floppy-disk" />
        </button>

        <button type="button" @click="cancelForm">
          <Icon name="fa6-solid:circle-xmark" />
        </button>
      </div>
    </form>
  </main>
</template>
<script>
export default {
  data() {
    return {
      formData: {
        title: "",
        name: "",
        surname: "",
        album: "",
        file: null,
      },
    };
  },
  methods: {
    storeData() {
      let users = JSON.parse(localStorage.getItem("users") || "[]");
      users.push({
        title: this.title,
        name: this.name,
        surname: this.surname,
        album: this.album,
      });
      localStorage.setItem("users", JSON.stringify(users));
    },
    submitForm() {
      console.log("Form submitted:", this.formData);
      window.location.href = "/documents";
    },
    cancelForm() {
      console.log("Form canceled");
      window.location.href = "/documents";
    },
    handleFileChange(event) {
      this.formData.file = event.target.files[0];
    },
  },
};
</script>
<style scoped lang="scss">
.formularz {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #555;
  padding: 10px 20px;
  text-decoration: none;
  border-radius: 10px;
  gap: 10px;
}
.text-input {
  background: none;
  border: none;
  border-bottom: 2px solid black;
  width: 100%;
  color: #bfdbf7;
  outline: none;
  font-size: 25px;
}
.text-input::placeholder {
  color: #bfdbf7;
}
.buttons {
  display: flex;
  gap: 40px;
}
button {
  background: none;
  border: none;
  cursor: pointer;
  border-radius: 30%;
  display: flex;
  padding: 5px;
  color: #bfdbf7;
  font-size: 35px;
}
input[type="file"] {
  display: none;
}
.custom-file-upload {
  background-color: #bfdbf7;
  text-align: left;
  font-size: 24px;
  border-radius: 10px;
  display: flex;
  padding: 10px 40px 10px;
  cursor: pointer;
  margin: 10px;
}
a {
  color: #bfdbf7;
  text-decoration: none;
}
</style>
