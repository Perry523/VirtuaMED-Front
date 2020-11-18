<template>
  <div class="row justify-center col-12">
    <div class="flex col-10 col-lg-3 col-md-4 col-sm-6">
      <div class="column full-width window-height">
        <div class="q-gutter-md col q-mb-lg">
          <label
            class="q-py-md row fill-height align-center justify-center"
            for="imgs"
          >
            <img
              :src="pessoa.img.path || placeholder"
              width="300px"
              height="300px"
              class="label img self-center"
              alt=""
          /></label>
          <input id="imgs" type="file" class="upload" @input="imgToUpload" />
          <q-select
            class="full-width"
            v-model="pessoa.nivel"
            :options="funcao"
            map-options
            emit-value
            label="Função"
          />
          <q-input class="full-width" v-model="pessoa.nome" label="Nome" />
          <q-input
            class="full-width"
            mask="###.###.###-##"
            v-model="pessoa.cpf"
            label="CPF"
          />
          <q-input
            class="full-width"
            v-model="pessoa.email"
            type="email"
            label="Email"
          />
          <div class="full-width" v-if="pessoa.nivel === 1">
            <div class="row full-width">
              <q-input
                class="col q-mr-sm"
                v-model="pessoa.coren"
                label="coren"
                mask="##-###.###-###"
              />
              <q-input
                class="col"
                v-model="pessoa.instituicao"
                label="Instituição"
              />
            </div>
          </div>
          <div class="full-width" v-if="pessoa.nivel === 2">
            <q-select
              v-model="pessoa.sangue"
              :options="sangue"
              label="Tipo sanguíneo"
            />
            <div class="row full-width">
              <q-input
                class="col q-mr-sm"
                v-model="pessoa.peso"
                label="Peso"
                mask="##,##"
                fill-mask="0"
                reverse-fill-mask
              />
              <q-input
                class="col"
                v-model="pessoa.altura"
                label="Altura"
                mask="#,##"
              />
            </div>
          </div>
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
              v-model="pessoa.password"
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
          <q-btn color="primary" class="full-width" @click="submit"
            >Cadastrar</q-btn
          >
          <q-btn to="/login" color="info" class="full-width q-my-sm"
            >Entrar</q-btn
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import logo from "components/Logo";
export default {
  name: "PageIndex",
  components: {
    // logo
  },
  data() {
    return {
      pessoa: {
        img: {}
      },
      funcao: [
        { label: "Médico", value: 1 },
        { label: "Paciente", value: 2 }
      ],
      sangue: [
        "A",
        "A+",
        "A-",
        "O",
        "O+",
        "O-",
        "B",
        "B+",
        "B-",
        "AB",
        "AB+",
        "AB-"
      ],
      placeholder:
        "https://i1.wp.com/spassodourado.com.br/wp-content/uploads/2015/01/default-placeholder.png"
    };
  },
  methods: {
    imgToUpload(e) {
      const file = e.target.files[0];
      if (!file) {
        return;
      }
      const reader = new FileReader();
      reader.onload = event => {
        file.path = event.target.result;
      };
      reader.readAsDataURL(file);
      setTimeout(() => {
        this.pessoa.img = file;
      }, 20);
      console.log(file);
    },
    submit() {
      const formData = new FormData();
      for (let data in this.pessoa) {
        formData.append(data, this.pessoa[data]);
      }
      this.$axios.post("/cadastro", formData);
    }
  }
};
</script>
<style>
.upload {
  display: none;
}
.label {
  cursor: pointer;
  border-radius: 3px;
}
.img {
  border-radius: 50%;
}
</style>
