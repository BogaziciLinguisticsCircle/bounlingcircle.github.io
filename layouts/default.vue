<template>
  <main>
    <div class="container">
      <div class="header">
        <h2>Boğaziçi University</h2>
        <h1>Linguistics Circle</h1>
        <p>
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab accusamus amet aspernatur delectus dolore doloribus dolorum harum nisi, optio porro quaerat repudiandae temporibus totam vel voluptas? Est eum id similique.
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Animi aperiam asperiores cupiditate ducimus eum ex exercitationem facere id iste modi molestiae mollitia obcaecati perspiciatis, sed sequi soluta unde ut, voluptatibus.
        </p>
        <img src="~/static/main.png" alt="Boğaziçi University Linguistic Circle image">
      </div>
      <div class="divider"></div>
      <div class="content">
        <Nuxt />
      </div>
    </div>
  </main>
</template>

<style lang="scss">
html, body {
  background-color: #fafafa;
  font-family: "Fira Sans", sans-serif;
  font-weight: 300;
  font-size: 14px;
    margin: 0;
    padding: 0;
}
@media screen and (orientation: portrait) {
  main { align-items: flex-start !important; }
  .container {
    max-width: 100% !important;
    width: 100% !important;
    flex-direction: column !important;
    .header {
      display: flex;
      flex-direction: row-reverse;
      align-items: center;
      justify-content: flex-start;
      .title {
        font-size: 40%;
        background-color: red;
      }
      h2 { display: none; }
      h1 {
        margin-left: 1rem;
        font-size: 1.25rem;
      }
      p { display: none; }
    }
  }
}
main {
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
.container {
  max-width: 1920px;
  width: 50%;
  max-height: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  img {
    margin-left: -5px;
    max-width: 100%;
  }
}
.divider {
  align-self: stretch;
  margin: 0 1em;
  border-left: 1px solid lightgray;
  border-right: 1px solid lightgray;
}
.header {
  max-width: 50%;
}
.content {
  max-width: 50%;
}
</style>
