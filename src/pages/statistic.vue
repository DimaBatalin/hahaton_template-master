<template>
    <q-page class="q-pa-lg">
      
      <q-table
      title="Статистика"
      :data="data"
      :columns="columns"
      row-key="name"
      :hide-bottom="data.length > 0"
      :rows-per-page-options="[0]"
    />  
    </q-page>
  </template>
  
  <script>
  export default {
    name: 'PageStatistic',
    methods: {

    },
    created: {
      
    },
    data() {
      return {
        columns: [
          {
            name: 'date',
            label: 'Дата',
            align: 'left',
            field: 'date',
            style: 'width: 1%',
          },
          {
            name: 'mans',
            required: true,
            label: 'Люди',
            align: 'left',
            field: 'mans',
            style: 'width: 10%',
          },
          {
            name: 'team',
            required: true,
            label: 'Тема',
            align: 'left',
            field: 'team',
            style: 'width: 15%',
          },
          {
            name: 'messages',
            required: true,
            label: 'Сообщения',
            align: 'left',
            field: 'messages',
            style: 'width: 30%',
          },
          {
            name: 'email',
            required: true,
            label: 'Email',
            align: 'left',
            field: 'email',
            style: 'width: 5%',
          },
          {
            name: 'telephoneNumber',
            required: true,
            label: 'Телефон',
            align: 'left',
            field: 'telephoneNumber',
            style: 'width: 5%',
          }
        ],
        data: [
          {
            date: '25.05.23',
            mans: "Баталин Дмитрий Андреевич", 
            team: "Поломка",
            messages: "Сломалось все, переделывай ",
            email: "email@vk.com",
            telephoneNumber: "89222222222",
          },
        ]
      }
    }
  }
  </script>
  