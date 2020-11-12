<template>
  <div class="row justify-center col-12">
    <div class="flex col-10 col-lg-3 col-md-4 col-sm-6 full-height">
      <div
        class="column full-width justify-center window-height	"
      >
        <logo col="5" />
        <div class="col-5">
          <q-input class="full-width" label="Email" />
          <q-input class="full-width" label="Senha" />
          <q-btn color="primary" class="full-width q-mt-lg q-mb-sm"
            >Entrar</q-btn
          >
          <q-btn to="/cadastrar" color="info" class="full-width"
            >Cadastrar</q-btn
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
  mounted() {
    console.log(this.$q);
  }
};
</script>
