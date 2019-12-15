<template>
  <q-page>
    <div class="window-height row justify-center items-center bg-grey">
      <q-card class="col-xs-12 col-sm-6">
        <q-card-section class="column q-gutter-x-md">
          <q-form @submit="sendForm">
            <p class="q-mb-sm"> Pesquisa </p>
            <q-select
              label="Qual etnia você considera que melhor te representa?"
              v-model="form.etnia"
              :options="options.etnia"
              dense
              :rules="[val => (val && val.length) || 'O campo é obrigatório.']"
              lazy-rules
            />
            <q-select
              label="Qual sua orientação sexual?"
              v-model="form.sexualOrientation"
              :options="options.sexualOrientation"
              dense
              :rules="[val => (val && val.length) || 'O campo é obrigatório.']"
              lazy-rules
            />
            <q-option-group
              label="De 1 a 5 (sendo 1 o menor e 5 o maior), quão heteronormativo você é?"
              v-model="form.heteronormativity"
              :options="options.heteronormativity"
              color="primary"
              inline
              dense
              :rules="[val => (val && val.length) || 'O campo é obrigatório.']"
              lazy-rules
            />
            <q-select
              label="Qual seu gênero?"
              v-model="form.genre"
              :options="options.genre"
              dense
              :rules="[val => (val && val.length) || 'O campo é obrigatório.']"
              lazy-rules
            />
            <q-btn
              label="enviar"
              color="cyan"
              type="submit"
              :disabled="
                !form.sexualOrientation || !form.heteronormativity || !form.etnia || !form.genre
              "
            />
          </q-form>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
export default {
  data: () => ({
    form: {
      etnia: '',
      sexualOrientation: '',
      heteronormativity: '',
    },
    options: {
      etnia: [
        'Branco', 'Negro', 'Pardo', 'Indígena',
      ],
      heteronormativity: [
        {
          label: '1',
          value: 1,
        },
        {
          label: '2',
          value: 2,
        },
        {
          label: '3',
          value: 3,
        },
        {
          label: '4',
          value: 4,
        },
        {
          label: '5',
          value: 5,
        },
      ],
      sexualOrientation: [
        'Assexual', 'Heterossexual', 'Homossexual', 'Bissexual/Pansexual',
      ],
      genre: [
        'Mulher Cis', 'Homem Cis', 'Mulher Trans', 'Homem Trans', 'Não Binário',
      ],
    },
    scores: {
      Branco: 0,
      Negro: 2,
      Indígena: 2,
      Pardo: 1,
      Amarelo: 0,
      Assexual: 0,
      Heterossexual: 0,
      Homossexual: 1,
      'Bissexual/Pansexual': 1,
      'Mulher Cis': 1,
      'Homem Cis': 0,
      'Mulher Trans': 2,
      'Homem Trans': 2,
      'Não binário': 1,
    },
  }),
  computed: {
    formattedQuery() {
      const {
        etnia, heteronormativity, sexualOrientation, genre,
      } = this.form;

      const lgbtScore = this.scores[heteronormativity * sexualOrientation];

      const form = {
        score0: this.scores[etnia], // racial
        score1: lgbtScore === 10 ? 2 : 1, // orientação
        score2: this.scores[genre], // genero
        company: this.$route.params.id,
      };

      return form;
    },
  },
  methods: {
    async sendForm() {
      this.$axios.post('/employee/add', this.formattedQuery);
    },
  },
};
</script>
