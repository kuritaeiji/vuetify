<template>
  <v-dialog v-model="dialog" max-width="500">
    <template #activator="{ on, attrs }">
      <v-btn dark depressed color="green accent-3" v-bind="attrs" v-on="on">
        add new project
      </v-btn>
    </template>

    <v-card flat>
      <v-card-title>add new project</v-card-title>

      <v-card-text class="text-center">
        <v-form ref="form">
          <v-text-field v-model="title" label="Title" prepend-icon="mdi-folder" :rules="inputRules" />
          <v-textarea v-model="info" label="Information" prepend-icon="mdi-pencil" :rules="inputRules" />
          <v-menu offset-y max-width="290">
            <template #activator="{ on, attrs }">
              <v-text-field
                v-model="due"
                label="Due date"
                prepend-icon="mdi-calender"
                :rules="datePicker.rules"
                v-bind="attrs"
                v-on="on"
              />
            </template>
            <v-date-picker
              v-model="due"
              :locale="datePicker.locale"
              :day-format="datePicker.dayFormat"
              :first-day-of-week="datePicker.firstDayOfWeek"
            />
          </v-menu>

          <v-btn dark depressed color="green acccent-3" :loading="loading" @click="submit">
            add product
          </v-btn>
        </v-form>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  data () {
    return {
      dialog: false,
      title: '',
      info: '',
      due: null,
      loading: false,
      datePicker: {
        locale: 'ja-jp',
        firstDayOfWeek: '1',
        dayFormat (date) {
          return new Date(date).getDate()
        },
        rules: [
          v => !!v || '日付を選択して下さい',
          v => /\d{4}-\d{2}-\d{2}/.test(v) || '正しいフォーマットで入力して下さい'
        ]
      },
      inputRules: [
        v => v.length >= 3 || '3文字以上入力して下さい'
      ]
    }
  },
  methods: {
    submit () {
      if (this.$refs.form.validate()) {
        this.loading = true
        console.log(this.title, this.info, this.due)
        const self = this
        setTimeout(() => {
          self.loading = false
          self.$emit('addedProduct', self.title)
          self.title = ''
          self.info = ''
          self.due = ''
          self.dialog = false
        }, 1000)
      }
    }
  }
}
</script>
