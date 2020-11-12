<template>
  <div class="row justify-center col-12">
    <div class="flex col-10 col-lg-3 col-md-4 col-sm-6">
      <div class="column full-width window-height">
        <logo col="3" />
        <div class="q-gutter-md col q-mb-lg">
          <q-input class="full-width" v-model="pessoa.nome" label="Nome" />
          <q-input
            class="full-width"
            mask="###.###.###-##"
            v-model="pessoa.CPF"
            label="CPF"
          />
          <q-input
            class="full-width"
            v-model="pessoa.email"
            type="email"
            label="Email"
          />
          <q-input
            class="full-width q-field--labeled q-field--float"
            v-model="pessoa.nascimento"
            type="date"
            label="Data de nascimento"
          />
          <q-input
            class="full-width"
            v-model="pessoa.telefone"
            type="tel"
            mask="(##) # ####-####"
            label="Telefone"
          />
          <div class="row full-width">
            <q-input
              class="col q-mr-sm"
              v-model="pessoa.senha"
              type="password"
              label="Senha"
            />
            <q-input
              class="col"
              v-model="pessoa.confirmarSenha"
              type="password"
              label="Confirmar Senha"
            />
          </div>
          <q-btn color="primary" class="full-width">Cadastrar</q-btn>
          <q-btn to="/login" color="info" class="full-width q-my-sm"
            >Entrar</q-btn
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import logo from "components/Logo";
export default {
  name: "PageIndex",
  components: {
    logo
  },
  data() {
    return {
      pessoa: {}
    };
  }
};
</script>
