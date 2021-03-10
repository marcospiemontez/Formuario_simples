<template>
  <q-page>
    <q-card class="container-principal row q-gutter-md">
      <div class="container-cadastro">
        <div class="container">
          <h2>CADASTRO</h2>
          <div>
            <q-card-section
              style="background: #dddd"
              class="col-md-6 col-sm-12 col-xs-12"
            >
              <div>
                <q-input
                  class="col-md-6 col-sm-12 col-xs-12"
                  type="text"
                  label="Nome"
                />
              </div>
              <div>
                <q-input
                  class="col-md-6 col-sm-12 col-xs-12"
                  type="email"
                  label="Email"
                />
              </div>
              <div>
                <q-input
                  class="col-md-6 col-sm-12 col-xs-12"
                  type="password"
                  label="Senha"
                />
              </div>
              <div>
                <q-input
                  class="col-md-6 col-sm-12 col-xs-12"
                  type="password"
                  label="Confirmar senha"
                />
              </div>
              <q-btn color="secondary" label="Cadastrar" padding="5px" />
            </q-card-section>
          </div>
        </div>
        <div class="container-login">
          <div>
            <h2>LOGIN</h2>
            <div>
              <q-card-section style="background: #dddd">
                <div>
                  <q-input
                    class="col-md-6 col-sm-12 col-xs-12"
                    type="text"
                    label="Email"
                  />
                </div>
                <div>
                  <q-input
                    class="col-md-6 col-sm-12 col-xs-12"
                    type="password"
                    label="Senha"
                  />
                </div>
                <q-btn color="secondary" label="Entrar" padding="5px" />
              </q-card-section>
            </div>
          </div>
        </div>
      </div>
    </q-card>
    <div id="controlador" class="controlador activeLogin">
      <div>
        <h1>Bem-Vindo</h1>
        <p>Olá, seja bem vindo(a) a maior rede de produtos veganos do Brasil</p>
        <button id="btnControlador">Fazer Cadastro</button>
      </div>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex'
}
</script>
