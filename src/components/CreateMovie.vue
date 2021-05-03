<template>
  <div>
      <b-form @submit="onSubmit" @reset="onReset">
      <b-form-group
        id="input-group-1"
        label="Movie Name:"
        label-for="input-1"
      >
        <b-form-input
          id="input-1"
          v-model="form.name"
          type="text"
          placeholder="Enter name"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Movie Director:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.director"
          placeholder="Enter Director"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Genre:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="form.genre"
          :options="genres"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-4" label="Movie Rating:" label-for="input-4">
        <b-form-input
          id="input-4"
          type="number"
          v-model="form.rating"
          placeholder="Enter Rating"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-5" label="Movie Release Data:" label-for="input-5">
        <b-form-input
          id="input-5"
          type="date"
          v-model="form.date"
          placeholder="Enter Release Date"
          required
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'CreateMovie',
  data(){
    return {
        form: {
          name: '',
          director: '',
          genre: null,
          rating: null,
          date: null,
        },
        genres: [{ text: 'Select One', value: null }, 'Action', 'Drama', 'Romance', 'Mystery'],
    }
  },
  computed: {
    
  },
  methods:{
    onSubmit(event) {
        event.preventDefault()
        axios.post('http://localhost:2500/movie',this.form)
            .then((res)=>{
                console.log(res)
            })
            .catch((err)=>{
                console.log(err)
            })
      },
      onReset(event) {
        event.preventDefault()
        // Reset our form values
        this.form.name = ''
        this.form.director = ''
        this.form.genre = null
        this.form.checked = []
        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      }
  }
}
</script>

