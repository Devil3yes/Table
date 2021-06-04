<template>
  <q-page padding>
    <div class="row q-mb-lg">
      <q-input v-model="add" placeholder="Add new Title" class="col"/>
      <q-btn color="primary" size="sm" label="Add" @click.native="addTask"/>
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
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      add: [],
      loading: false,
      newTask: '',
      rowCount: 10,
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
        { name: 'years', label: 'Carbs (g)', field: 'carbs' }
      ],
      data: [
        {
          name: 'Frozen Yogurt',
          calories: 159,
          fat: 6.0,
          carbs: 24
        },
        {
          name: 'Ice cream sandwich',
          calories: 237,
          fat: 9.0,
          carbs: 37
        },
        {
          name: 'Eclair',
          calories: 262,
          fat: 16.0,
          carbs: 23
        }
      ]
    }
  },
  methods: {
    addTask () {
      this.add.push(this.newTask)
      this.newTask = ''
      this.loading = true
      setTimeout(() => {
        const
          index = Math.floor(Math.random() * (this.data.length + 1)),
          row = this.original[Math.floor(Math.random() * this.original.length)]
        if (this.data.length === 0) {
          this.rowCount = 0
        }
        row.id = ++this.rowCount
        const addRow = { ...row } // extend({}, row, { name: `${row.name} (${row.__count})` })
        this.data = [ ...this.data.slice(0, index), addRow, ...this.data.slice(index) ]
        this.loading = false
      }, 500)
    },
    removeTask () {
      self.removeLine = function () {
        self.koData.remove(this);
      }
    }
  }
}
</script>
