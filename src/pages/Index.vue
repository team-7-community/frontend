<template>
  <q-page class="row flex-center">
    <div class="col-xs-12 col-md-8 row q-gutter-md justify-center q-px-md">
      <q-card
        class="col-xs-12 col-sm-3"
        v-for="(company, index) in companies"
        :key="index"
      >
        <q-card-section>
          <div> {{ company.name }} {{ index + 1 }} </div>
          <div class="flex">
            <div
              v-for="(badge, index) in company.badges"
              :key="index"
            >
              <badge v-bind="badge"/>
            </div>
          </div>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import Badge from '../components/Badge.vue';

export default {
  components: {
    Badge,
  },
  data: () => ({
    companies: [
      {
        name: 'Empresa',
        badges: [
          {
            value: Math.floor(Math.random() * 100),
            type: 'Orientação Sexual',
          },
          {
            value: Math.floor(Math.random() * 100),
            type: 'Gênero',
          },
          {
            value: Math.floor(Math.random() * 100),
            type: 'Racial',
          },
        ],
      },
      {
        name: 'Empresa',
        badges: [
          {
            value: Math.floor(Math.random() * 100),
            type: 'Orientação Sexual',
          },
          {
            value: Math.floor(Math.random() * 100),
            type: 'Gênero',
          },
          {
            value: Math.floor(Math.random() * 100),
            type: 'Racial',
          },
        ],
      },
      {
        name: 'Empresa',
        badges: [
          {
            value: Math.floor(Math.random() * 100),
            type: 'Orientação Sexual',
          },
          {
            value: Math.floor(Math.random() * 100),
            type: 'Gênero',
          },
          {
            value: Math.floor(Math.random() * 100),
            type: 'Racial',
          },
        ],
      },
      {
        name: 'Empresa',
        badges: [
          {
            value: Math.floor(Math.random() * 100),
            type: 'Orientação Sexual',
          },
          {
            value: Math.floor(Math.random() * 100),
            type: 'Gênero',
          },
          {
            value: Math.floor(Math.random() * 100),
            type: 'Racial',
          },
        ],
      },
      {
        name: 'Empresa',
        badges: [
          {
            value: Math.floor(Math.random() * 100),
            type: 'Orientação Sexual',
          },
          {
            value: Math.floor(Math.random() * 100),
            type: 'Gênero',
          },
          {
            value: Math.floor(Math.random() * 100),
            type: 'Racial',
          },
        ],
      },
    ],
  }),
};
</script>
