<template>
  <!-- o q-page é obrigatório quando há paginas! -->
  <q-page class="conteiner" padding>
    <!-- foi criado um texto em 'formato' de título -->
    <p class="text-h4 text-center">Formulário</p>
    <!-- para criação de formulários é sempre interessante ter essa tag 'q-form' -->
    <q-form
      @submit="onSubmit"
      @reset="onReset"
      ref="myForm"
      class="row q-gutter-md flex flex-center"
    >
      <!-- o @submit e o @reset está ligando à lógica JS feita la em baixo, o 'ref="myForm"' foi feito para referenciar ao clear do formulário ao concluir. -->
      <q-input
        outlined
        color="deep-purple"
        v-model="form.nome"
        label="Nome"
        class="col-md-6 col-sm-12 col-xs-12"
        :rules="[val => (val && val.length > 0) || 'Nome obrigatório']"
      >
        <!-- o input de cima foi feito para o nome da pessoa, v-model=form.nome liga ao JS la em baixo, :rules é a lógica implantada -->
        <!-- o template abaixo clia um icone na linha do input, sendo o v-slot:prepend aplica o icone no inicio do input,  -->
        <template v-slot:prepend>
          <q-icon name="person" />
        </template>
      </q-input>
      <!-- input do botão de idade, o :rules traz a lógica que "valor recebe valor diferente de null e diferente de vazio
      valor recebe valor e valor tem q ser maior que 0 e menor q 100" -->
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
      <!-- rules: valor recebe valor e valor tem q ter o comprimento maios que 0 -->
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
      <!-- rules, valor recebe valor e valor tem q ser maior que 0,
      rules valor recebe valor e e tem q ser igual a 11 digitos -->
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
          <!-- esse prepende faz com que o icone fique no inicio do input, p/ por no final do input seria "append" -->
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
