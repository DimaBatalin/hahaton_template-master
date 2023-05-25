<template>
  <q-page class="q-pa-lg">

    <q-btn text-color="black" label="Добавить сообщение" class="q-mb-lg bg-accent" @click="isVisibl = !isVisibl"/>

    <q-table
      title="Сообщения"
      :data="data"
      :columns="columns"
      row-key="name"
      :hide-bottom="data.length > 0"
      :rows-per-page-options="[0]"
    />  

    <q-dialog v-model="isVisibl" @before-hide="closeMessageDialog">
      <q-card style="width: 500px; max-width: 90vw;" class="bg-white">
        <q-card-section class="row items-center">
          <div class="col text-h5">Добавление сообщения</div> 
          
          <div class="col-auto">
            <q-btn
              v-close-popup
              icon="close"
              color="dark"
              flat
            />
          </div>
          
        </q-card-section>

        <q-separator />

        <q-card-section>
          <q-input v-model="message.subject" placeholder="Тема"/>
          <q-input v-model="message.body" placeholder="Сообщение"/>
          <div style="display: flex" class="q-ma-md">
            <q-select
            filled
            v-model="message.sensors"
            multiple
            :options="options"
            label="Датчики"
            style="width: 250px"
            /> 
            <q-btn color="orange" text-color="black" label="Добавить" class="q-ml-md" @click="addMessage"/>
          </div>
        </q-card-section>
      </q-card>
    </q-dialog>


  </q-page>
</template>

<script>

export default {
  name: 'PageIndex',
  data() {
    return {
      message: {
        subject: null,
        body: null,
        sensors: null,
      },
      options: [
        '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12', '13', '14', '15', '16', '17', '18'
      ],
      isVisibl: false,
      columns: [
          {
            name: 'number',
            label: 'Номер',
            align: 'left',
            field: 'number',
            style: 'width: 1%',
          },
          {
            name: 'subject',
            required: true,
            label: 'Тема',
            align: 'left',
            field: 'subject',
            style: 'width: 30%',
          },
          {
            name: 'body',
            required: true,
            label: 'Содержимое',
            align: 'left',
            field: 'body',
            style: 'width: 40%',
          },
          {
            name: 'sensors',
            required: true,
            label: 'Датчики',
            align: 'left',
            field: 'sensors',
          }
      ],
      data: [
        {
          number: 1,
          subject: "поломка", 
          body: "надо печенить",
          sensors: "12"
        },
        {
          number: 2,
          subject: "поломка", 
          body: "надо печенить",
          sensors: "34"
        },
        {
          number: 3,
          subject: "поломка", 
          body: "надо печенить",
          sensors: "56"
        },
        {
          number: 4,
          subject: "всё хорошо", 
          body: "проверь плз",
          sensors: "67"
        },
      ]
    }
  },
  methods: {
    closeMessageDialog() {
      this.message.subject = null
      this.message.body = null
      this.message.sensors = null
    },
    addMessage() {
      this.data.push({
        number: this.data.length + 1,
        ...this.message,
      })
      this.isVisibl = false
      this.closeMessageDialog()
    }
  }
}
</script>
