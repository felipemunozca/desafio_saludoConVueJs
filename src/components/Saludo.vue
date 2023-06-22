<template>
    <div class="container form-section">
        <!-- 
            Al utilizar la etiqueta <form> el formulario se recarga al presionar el botón registrar.
            Se cambia <form> por <div> y queda pendiente averiguar como evitar que se recargue el formulario.
        -->
        <div class="col-12 col-md-8 m-auto">
            <h2 class="mb-4">Formulario Saludo</h2>
            <div class="row mb-4">
                <label for="" class="col-sm-2 col-form-label">Nombre</label>
                <div class="col-sm-10">
                    <input v-model='inputNombre' type="text" class="form-control" id="" placeholder="Ingrese su nombre.">
                </div>
            </div>
            <div class="row mb-4">
                <label for="" class="col-sm-2 col-form-label">Apellido</label>
                <div class="col-sm-10">
                    <input v-model='inputApellido' type="text" class="form-control" id="" placeholder="Ingrese su apellido.">
                </div>
            </div>
            <div class="row mb-4">
                <label for="" class="col-sm-2 col-form-label">Correo</label>
                <div class="col-sm-10">
                    <input v-model='inputCorreo' type="email" class="form-control" id="" placeholder="Ingrese su correo.">
                </div>
            </div>
            <div class="row mb-4">
                <label for="" class="col-sm-2 col-form-label">Edad</label>
                <div class="col-sm-10">
                    <input v-model='inputEdad' type="number" class="form-control" id="" placeholder="Ingrese su edad.">
                </div>
            </div>

            <button @click='btnRegistrar' type="" class="btn btn-primary">Registrar</button>

            <!--  
                Se utilizan las directivas v-if y v-else-if para evaluar el valor de inputEdad.
                Dependiendo del numero escrito, se imprimirá un mensaje debajo del botón indicando el rango etario del usuario.
            -->
            <div v-if="registrado" class="response-section">
                <div v-if="inputEdad > 0 && inputEdad < 14">
                    Eres un niño.
                </div>

                <div v-else-if="inputEdad > 13 && inputEdad < 18">
                    Eres un adolescente.
                </div>

                <div v-else-if="inputEdad > 17 && inputEdad < 36">
                    Eres un adulto joven.
                </div>

                <div v-else-if="inputEdad > 34 && inputEdad < 65">
                    Eres un adulto.
                </div>

                <div v-else-if="inputEdad > 65">
                    Eres un adulto mayor.
                </div>
            </div>
        </div>
    </div>
    
</template>

<script>
export default {
    name: 'saludo-alert',
    // props: {},
    data: function(){
        return {
            /**
             * Se declaran las variables obtenidas desde cada input del formulario.
             * Ademas, se crea una propiedad "registrado" la cual sera un booleano y se utilizara en la directiva v-if para revisar
             * si el usuario ya completo el formulario, su valor cambiara a true, y luego se podrá revisar la condición de edad.
             */
            inputNombre: '',
            inputApellido: '',
            inputCorreo: '',
            inputEdad: '', 
            registrado: false,
        }
    },
    // computed: {},
    methods: {
        btnRegistrar(){

            /* Guardianes. */
            if(this.inputNombre == ''){
                alert ('El campo nombre es requerido.')
                return
            }
            if(this.inputApellido == ''){
                alert ('El campo apellido es requerido.')
                return
            }
            if(this.inputCorreo == ''){
                alert ('El campo correo es requerido.')
                return
            }
            if(this.inputEdad == ''){
                alert ('El campo edad es requerido.')
                return
            }

            let saludo = `Saludos ${this.inputNombre} ${this.inputApellido}.\nTu correo es: ${this.inputCorreo}`;

            alert(saludo);

            this.registrado = true;
        }


    }
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    .form-section {
        background-color: lightcyan;
        padding: 40px 50px;
        border-radius: 5px;
    }
    .response-section {
        background-color: lightgreen;
        padding: 10px;
        width: 300px;
        text-align: center;
        margin: 30px auto 0;
        border: 1px solid white;
    }
</style>