<template>
    <div class="hello">
        <h3>{{title}}</h3>
        <b-form @submit="onSubmit" v-if="show" class="text-left formulario mx-auto float">
            <b-form-group
                id="input-group-1"
                label="Título"
                label-for="input-1"
            >
                <b-form-input
                    id="input-1"
                    v-model="form.title"
                    placeholder="Ingresa texto"
                ></b-form-input>
            </b-form-group>

        <b-form-group id="input-group-2" label="Elige un filtro:" label-for="input-2">
            <b-form-select
                id="input-2"
                v-model="form.filter"
                :options="filters"
            ></b-form-select>
        </b-form-group>

        <b-form-group id="input-group-3" label="Color del texto:" label-for="input-3">
            <b-form-select
                id="input-3"
                v-model="form.color"
                :options="colors"
            ></b-form-select>
        </b-form-group>

        <b-form-group id="input-group-3" label="Tamaño del texto:" label-for="input-4">
            <!-- <b-form-select
                id="input-4"
                v-model="form.size"
                :options="sizes"
                required
            ></b-form-select> -->
            <b-form-input
                    id="input-4"
                    v-model="form.sizeNum"
                    placeholder="Ingresa Tamaño del texto"
            ></b-form-input>
        </b-form-group>

        <div class="d-flex justify-content-center">
            <b-button type="submit" variant="success">Submit</b-button>
        </div>
        <!-- <b-button type="reset" variant="danger">Reset</b-button> -->
        </b-form>

        <!-- <b-card class="mt-3" header="Sacame cuando termines">
            <pre class="m-0">{{ form }}</pre>
        </b-card> -->
        <b-card
            title=""
            :img-src="gifURL"
            img-alt="Image"
            img-top
            tag="article"
            
            class="mb-2 mx-auto float w-75"
        ></b-card>

    </div>
</template>


<script>
export default {
    name: 'Formulario',
    props: {
        msg: String,
    },
    data() {
        return {
            title: `Generador de gif de gatitos! \\(@^0^@)/`,
            form: {
                title: '',
                filter: null,
                color: '%23FFF',
                sizeNum: '',
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
                {text: 'Blanco', value: '%23FFF'}, 
                {text: 'Negro', value: '%23000'},
                {text: 'Gris', value: '%23888'},
                {text: 'Rojo', value: '%23E30B2D'},
                {text: 'Naranjo', value: '%23D95B0B'}, 
                {text: 'Azul', value: '%230B35D9'}, 
                {text: 'Verde', value: '%2340CC00'}, 
                {text: 'Amarillo', value: '%23E3C20B'}, 
                {text: 'Morado', value: '%23710BE3'}, 
            ],
            show: true,
            gifURL: 'https://picsum.photos/600/300/?image=23',

        }
    },
    methods: {
        onSubmit(evt) {
            evt.preventDefault()
            // alert(JSON.stringify(this.form))
            this.displayGif(this.form.title, this.form.filter, this.form.color, this.form.sizeNum)
        },
        displayGif(title, filter, color, size) {

            const gifApiCall = async (t, f, c, s) => {
                console.log(this.gifURL)
                try {
                    let fetchURL = `https://cataas.com/cat/gif/says/${t}?filter=${f}&color=${c}&size=${s}`;
                    let res = await fetch(fetchURL);
                    console.log(`la url es ${res.url}`);
                    if(res.status === 200) {
                        this.gifURL = res.url;
                        console.log(`la url está correcta`)
                    }
                } catch (error) {
                    console.error(error);
                }
            }
            this.gifURL = gifApiCall(title, filter, color, size)
            console.log(this.gifURL)
        },
    },
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
