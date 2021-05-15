<template>
  <q-page padding>
    <div class="row q-mb-lg">
      <q-input v-model="add" placeholder="Add new Title" class="col" @keyup.enter="add"/>
      <q-btn color="primary" size="sm" label="Add" @click.native="add"/>
    </div>
    <div class="row justify-evenly">
      <q-list hight class="col">
        <q-list-header>Task</q-list-header>
        <q-item v-font="newTask in add">
          <q-item-main :label="addTask"/>
          <q-item-side right icon="Check" color="secondary"/>
        </q-item>
      </q-list>
    </div>
    <div class="q-pa-md">
    <q-table
      title="Table"
      :data="data"
      :columns="columns"
      row-key="name"
      hide-header
      hide-bottom/>
  </div>
  <q-page-sticky position="bottom-right"  :offset="[45,178]">
    <q-btn class="btn-add-right" round color="primary" icon="add"/>
  </q-page-sticky>
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      framework: {
        plugins: [
          'Cookies']
      },
      add: [],
      newTask: '',
      columns: [
        {
          name: 'name',
          required: true,
          label: 'Dessert (100g serving)',
          align: 'left',
          field: row => row.name,
          format: val => `${val}`,
          sortable: true
        },
        { name: 'calories', align: 'center', label: 'Calories', field: 'calories', sortable: true },
        { name: 'fat', label: 'Fat (g)', field: 'fat', sortable: true },
        { name: 'carbs', label: 'Carbs (g)', field: 'carbs' },
        { name: 'protein', label: 'Protein (g)', field: 'protein' },
        { name: 'sodium', label: 'Sodium (mg)', field: 'sodium' }],
      data: [
        {
          name: 'Frozen Yogurt',
          calories: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
          sodium: 87
        },
        {
          name: 'Ice cream sandwich',
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          sodium: 129
        },
        {
          name: 'Eclair',
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          sodium: 337
        }
      ]
    }
  },
  methods: {
    addTask () {
      this.add.push(this.newTask)
      this.newTask = ''
    }
  }
}
</script>
