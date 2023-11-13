<template>
  <header><NuxtLink to="/">Biuro Obsługi Studenta</NuxtLink></header>
  <main>
    <h1>WNIOSKI</h1>
    <div class="list">
      <div class="list-element">
        <span>
          <div class="title">Wniosek o stypendium</div>
          <div class="info">Jan Kowalski 654343</div>
        </span>
        <div class="buttons">
          <NuxtLink to="/document-form"
            ><button title="Edytuj wniosek"><Icon name="fa-solid:pen" /></button
          ></NuxtLink>
          <button title="Usuń wniosek">
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
