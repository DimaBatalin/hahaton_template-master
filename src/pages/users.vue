<template>
  <q-page class="q-pa-lg">

    <q-btn text-color="black" label="Добавить пользователя" class="q-mb-lg bg-accent" @click="isVisiblUser = !isVisiblUser"/>

    <q-table
      title="Пользователи"
      :data="data"
      :columns="columns"
      row-key="name"
      :hide-bottom="data.length > 0"
      :rows-per-page-options="[0]"
    />  

    <q-dialog v-model="isVisiblUser">
      <q-card style="width: 500px; max-width: 90vw;" class="bg-white">
        <q-card-section class="row items-center">
          <div class="col text-h5">Добавление пользователя</div> 
          
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
          <q-input v-model="message.name" placeholder="ФИО"/>
          <q-input v-model="message.email" placeholder="Email"/>
          <q-input v-model="message.telephoneNumber" placeholder="Номер телефона"/>

          <div style="display: flex" class="q-ma-md">
            <q-select
              filled
              multiple
              :options="options"
              label="Датчики"
              style="width: 250px"
              v-model="message.sensors"
            /> 
            <q-btn color="orange" text-color="black" label="Добавить" @click="addMessage()" class="q-ml-md"/>
          </div>
        </q-card-section>
      </q-card>
    </q-dialog>
  </q-page>
</template>
  
<script>
export default {
  name: 'PageUsers',
  data() {
    return {
      isVisiblUser: false,
      options: [
        '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12', '13', '14', '15', '16', '17', '18'
      ],
      columns: [
        {
          name: 'number',
          label: 'Номер',
          align: 'left',
          field: 'number',
          style: 'width: 1%',
        },
        {
          name: 'name',
          required: true,
          label: 'Фио',
          align: 'left',
          field: 'name',
          style: 'width: 15%',
        },
        {
          name: 'telephoneNumber',
          required: true,
          label: 'Номер телефона',
          align: 'left',
          field: 'telephoneNumber',
          style: 'width: 40%',
        },
        {
          name: 'email',
          required: true,
          label: 'Email',
          align: 'left',
          field: 'email',
        },
        {
          name: "sensors",
          required: true, 
          label: "sensors",
          align: "left", 
          field: "sensors",
          style: "width: 10%"
        },
      ],
      data: [
        {
          number: 1,
          name: "Баталин Сергей Андреевич", 
          telephoneNumber: "892212.....",
          email: "sensors1@gmail.com",
          sensors: "1, 2, 3",
        },
        {
          number: 2,
          name: "Костин Сергей Андреевич", 
          telephoneNumber: "892122.....",
          email: "sensors2@gmail.com",
          sensors: "1, 2, 3",
        },
        {
          number: 3,
          name: "Костин Сергей Семенович", 
          telephoneNumber: "892112.....",
          email: "sensors3@gmail.com",
          sensors: "1, 2, 3",
        },
        {
          number: 4,
          name: "Баталин Дмитрий Андреевич", 
          telephoneNumber: "892222.....",
          email: "sensors4@gmail.com",
          sensors: "1, 2, 3",
        },
      ],
      message: {
        name: null,
        telephoneNumber: null,
        email: null,
        sensors: null
      },
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
