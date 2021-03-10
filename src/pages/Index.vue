<template>
  <q-page class="conteiner" padding>
    <p class="text-h4 text-center">Formulário</p>
    <q-form
      @submit="onSubmit"
      @reset="onReset"
      ref="myForm"
      class="row q-gutter-md flex flex-center"
    >
      <q-input
        outlined
        color="deep-purple"
        v-model="form.nome"
        label="Nome"
        class="col-md-6 col-sm-12 col-xs-12"
        :rules="[val => (val && val.length > 0) || 'Nome obrigatório']"
      >
        <template v-slot:prepend>
          <q-icon name="person" />
        </template>
      </q-input>
      <q-input
        outlined
        color="deep-purple"
        v-model.number="form.idade"
        type="number"
        label="Idade"
        class="col-md-6 col-sm-12 col-xs-12"
        :rules="[
          val => (val !== null && val !== '') || 'Idade obrigatória',
          val => (val > 0 && val < 100) || 'Coloque uma idade real'
        ]"
      >
        <template v-slot:prepend>
          <q-icon name="person" />
        </template>
      </q-input>
      <q-input
        outlined
        color="deep-purple"
        v-model="form.email"
        type="email"
        label="Email"
        class="col-md-6 col-sm-12 col-xs-12"
        :rules="[val => (val && val.length > 0) || 'Email obrigatório']"
      >
        <template v-slot:prepend>
          <q-icon name="mail" />
        </template>
      </q-input>
      <q-input
        outlined
        color="deep-purple"
        v-model="form.telefone"
        label="Telefone"
        mask="(##) #####-####"
        unmasked-value
        class="col-md-6 col-sm-12 col-xs-12"
        :rules="[
          val => (val && val.length > 0) || 'Telefone obrigatório',
          val => val.length === 11 || 'Coloque telefone real'
        ]"
      >
        <template v-slot:prepend>
          <q-icon name="call" />
        </template>
      </q-input>
      <q-select
        class="col-md-6 col-sm-12 col-xs-12"
        outlined
        v-model="form.TipoPessoa"
        :options="optionsTipoPessoa"
        label="Tipo de pessoa"
        emit-value
        map-options
        :rules="[
          val => (val && val.length > 0) || 'Tipo de Pessoa obrigatório'
        ]"
      />
      <span class="col-md-6 col-sm-12 col-xs-12 float-right q-pr-lg text-bold"
        >Sexo</span
      >
      <q-option-group
        :options="optionsSexo"
        label="Sexo"
        type="radio"
        v-model="form.sexo"
        class="col-md-6 col-sm-12 col-xs-12 float-right q-mr-lg"
      />
      <div class="col-md-6 col-sm-12 col-xs-12">
        <q-btn
          label="Cadastrar"
          type="submit"
          color="deep-purple"
          class="float-right"
        />

        <q-btn
          label="Resetar"
          type="reset"
          color="deep-purple"
          flat
          class="col-md-6 col-sm-12 col-xs-12 float-right q-mr-lg"
        />
      </div>
    </q-form>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      form: {
        nome: '',
        idade: null,
        email: '',
        telefone: '',
        TipoPessoa: '',
        sexo: 'NI'
      },
      optionsTipoPessoa: [
        { label: 'Pessoa Física', value: 'pf' },
        { label: 'Pessoa Jurídica', value: 'pj' }
      ],
      optionsSexo: [
        { label: 'Não Informado', value: 'NI' },
        { label: 'Masculino', value: 'M' },
        { label: 'Feminino', value: 'F' }
      ]
    }
  },
  methods: {
    onSubmit () {
      this.$q.notify({
        message: 'Cadastro realizado com sucesso',
        color: 'positive',
        icon: 'check_circle'
      })
      this.onReset()
    },

    async onReset () {
      await this.resetForm()
      this.$refs.myForm.resetValidation()
    },
    async resetForm () {
      this.form = {
        nome: '',
        idade: null,
        email: '',
        telefone: '',
        TipoPessoa: '',
        sexo: 'NI'
      }
    }
  }
}
</script>
