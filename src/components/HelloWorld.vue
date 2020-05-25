<template>
  <div class="hello">
    <h3>{{title}}</h3>
    <b-form @submit="onSubmit" @reset="onReset" v-if="show" class="text-left formulario mx-auto float">
      <b-form-group
        id="input-group-1"
        label="Título"
        label-for="input-1"
      >
        <b-form-input
          id="input-1"
          v-model="form.title"
          required
          placeholder="Ingresa texto"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Elige un filtro:" label-for="input-2">
        <b-form-select
          id="input-2"
          v-model="form.filter"
          :options="filters"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-3" label="Color del texto:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="form.color"
          :options="colors"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-3" label="Color del texto:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="form.color"
          :options="colors"
          required
        ></b-form-select>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    <b-card class="mt-3" header="Sacame cuando termines">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
  </div>
</template>

<script>
export default {
    name: 'HelloWorld',
    props: {
        msg: String,
    },
    data() {
        return {
            title: `Generador de gif de gatitos! \\(@^0^@)/`,
            form: {
                title: '',
                filter: null,
                color: '#FFF',
            },
            filters: [
                {text: 'Ningún Filtro Seleccionado', value: null}, 
                {text: 'Borroso', value: 'blur'},
                {text: 'Monocromático', value: 'mono'}, 
                {text: 'Sepia', value: 'sepia'}, 
                {text: 'Negativo', value: 'negative'}, 
                {text: 'Pintura', value: 'paint'}, 
                {text: 'Pixeleado', value: 'pixel'}, 
            ],
            colors: [
                {text: 'Blanco', value: '#FFF'}, 
                {text: 'Negro', value: '#000'},
                {text: 'Gris', value: '#888'},
                {text: 'Rojo', value: '#E30B2D'},
                {text: 'Naranjo', value: '#D95B0B'}, 
                {text: 'Azul', value: '#0B35D9'}, 
                {text: 'Verde', value: '#40CC00'}, 
                {text: 'Amarillo', value: '#E3C20B'}, 
                {text: 'Morado', value: '#710BE3'}, 
            ],
            show: true
        }
    },
    methods: {
        onSubmit(evt) {
            evt.preventDefault()
            alert(JSON.stringify(this.form))
        },
        onReset(evt) {
            evt.preventDefault()
            // Reset our form values
            this.form.email = ''
            this.form.name = ''
            this.form.food = null
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.text-left {
    text-align: left;
}
.formulario {
    background-color: rgb(255, 250, 245);
    margin: 16px;
    padding: 32px 64px;
    box-shadow: 2px 4px 6px rgba(128, 128, 128, 0.2);
    max-width: 600px;
}

</style>
