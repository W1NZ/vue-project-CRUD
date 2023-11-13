<template>
  <header>Biuro Obsługi Studenta</header>
  <main>
    <h1>TRYB EDYCJI</h1>
    <form @submit.prevent="submitForm" class="formularz">
      <div>
        <input
          class="text-input"
          type="text"
          id="title"
          v-model="formData.title"
          required
          placeholder="TYTUŁ"
        />
      </div>
      <div>
        <input
          class="text-input"
          type="text"
          id="name"
          v-model="formData.name"
          required
          placeholder="IMIĘ"
        />
      </div>
      <div>
        <input
          class="text-input"
          type="text"
          id="surname"
          v-model="formData.surname"
          required
          placeholder="NAZWISKO"
        />
      </div>
      <div>
        <input
          class="text-input"
          type="text"
          id="index"
          v-model="formData.index"
          required
          placeholder="NR ALBUMU"
        />
      </div>
      <div>
        <label for="file" class="custom-file-upload"> ZAŁĄCZ PLIK </label>
        <input type="file" id="file" @change="handleFileChange" />
      </div>
      <div class="buttons">
        <NuxtLink to="/documents"
          ><button type="submit"><Icon name="fa6-solid:floppy-disk" /></button
        ></NuxtLink>
        <NuxtLink to="/documents"
          ><button type="button" @click="cancelForm">
            <Icon name="fa6-solid:circle-xmark" /></button
        ></NuxtLink>
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
        index: "",
        file: null,
      },
    };
  },
  methods: {
    submitForm() {
      // Handle form submission logic
      console.log("Form submitted:", this.formData);
    },
    cancelForm() {
      // Handle form cancellation logic
      console.log("Form canceled");
    },
    handleFileChange(event) {
      // Handle file change logic
      this.formData.file = event.target.files[0];
    },
  },
};
</script>
<style scoped>
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
  font-size: 20px;
}
input[type="file"] {
  display: none;
}
.custom-file-upload {
  background-color: #bfdbf7;
  text-align: left;
  font-size: 16px;
  border-radius: 10px;
  display: flex;
  padding: 10px 40px 10px;
  cursor: pointer;
  margin: 10px;
}
</style>
