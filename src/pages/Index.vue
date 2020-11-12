<template>
  <div class="row justify-center col-12 full-height">
    <div class="flex col-11 col-lg-3 col-md-4 col-sm-6 full-height">
      <div class="column full-width window-height">
        <logo />
        <q-btn to="/login" color="primary" class="full-width q-mb-sm">Entrar</q-btn>
        <q-btn to="/cadastrar" color="info" class="full-width">Criar Conta</q-btn>
      </div>
    </div>
  </div>
</template>

<script>
import logo from 'components/Logo'
export default {
  name: "PageIndex",
  components: {
    logo
  }
};
</script>
