<template>
    <div>
        <b-container fluid>
            <b-row>
                <b-col cols="12" class="p-3">
                    <b-card class="pt-3 pb-5 px-3">
                        <b-form @submit.prevent="onSubmit">
                            <b-card header-tag="header" class="mb-4">
                                <template #header>
                                    <h5 class="mb-0">Información personal</h5>
                                </template>
                                <b-card-body>
                                    <b-row>
                                        <b-col cols="12" md="4" align-self="center">
                                            <b-img :src="showImg()" class="img" alt="Imagen seleccionada" fluid rounded center></b-img>
                                            <b-form-group>
                                                <b-form-file id="img" class="mt-3"></b-form-file>
                                            </b-form-group>
                                        </b-col>
                                        <b-col cols="12" md="8">
                                            <b-list-group flush>
                                                <b-list-group-item>
                                                    <b-row>
                                                        <b-col cols="12" md="6" class="mt-3 mt-md-0">
                                                            <b-form-group>
                                                                <label for="name" class="mb-2">Nombre:</label>
                                                                <b-form-input id="name" placeholder="Escriba su nombre..."
                                                                ></b-form-input>
                                                            </b-form-group>
                                                        </b-col>
                                                        <b-col cols="12" md="6" class="mt-3 mt-md-0">
                                                            <b-form-group>
                                                                <label for="surname" class="mb-2">Apellido paterno:</label>
                                                                <b-form-input id="surname"
                                                                    placeholder="Escriba su apellido paterno..."
                                                                ></b-form-input>
                                                            </b-form-group>
                                                        </b-col>
                                                    </b-row>
                                                    <b-row class="pb-4">
                                                        <b-col cols="12" md="6" class="mt-3">
                                                            <b-form-group>
                                                                <label for="lastname" class="mb-2">Apellido materno:</label>
                                                                <b-form-input id="lastname"
                                                                    placeholder="Escriba su apellido materno..."></b-form-input>
                                                            </b-form-group>
                                                        </b-col>
                                                        <b-col cols="12" md="6" class="mt-3">
                                                            <b-form-group>
                                                                <label for="birthdate" class="mb-2">Fecha de nacimiento:</label>
                                                                <b-form-input id="birthdate" type="date"
                                                                ></b-form-input>
                                                            </b-form-group>
                                                        </b-col>
                                                    </b-row>
                                                </b-list-group-item>
                                                <b-list-group-item>
                                                    <b-row>
                                                        <b-col cols="12" md="6" class="mt-3">
                                                            <b-form-group>
                                                                <label for="email" class="mb-2">Correo electrónico:</label>
                                                                <b-form-input id="email" type="email"
                                                                    placeholder="Escriba su correo electrónico..."
                                                                ></b-form-input>
                                                            </b-form-group>
                                                        </b-col>
                                                        <b-col cols="12" md="6" class="mt-3">
                                                            <b-form-group>
                                                                <label for="birthdate" class="mb-2">Teléfono:</label>
                                                                <b-form-input id="birthdate" type="tel"
                                                                    placeholder="Escriba su número de teléfono..."
                                                                ></b-form-input>
                                                            </b-form-group>
                                                        </b-col>
                                                    </b-row>
                                                </b-list-group-item>
                                            </b-list-group>
                                        </b-col>
                                    </b-row>
                                </b-card-body>
                            </b-card>
                            <b-card header-tag="header" class="mb-4">
                                <template #header>
                                    <h5 class="mb-0">Dirección</h5>
                                </template>
                                <b-card-body>
                                    <b-row>
                                        <b-col cols="12" md="4">
                                            <b-form-group>
                                                <label for="country" class="mb-2">País:</label>
                                                <b-form-input id="country" placeholder="Escriba su país..."
                                                ></b-form-input>
                                            </b-form-group>
                                        </b-col>
                                        <b-col cols="12" md="4" class="mt-3 mt-md-0">
                                            <b-form-group>
                                                <label for="state" class="mb-2">Estado:</label>
                                                <b-form-input id="state" placeholder="Escriba su estado..."
                                                ></b-form-input>
                                            </b-form-group>
                                        </b-col>
                                        <b-col cols="12" md="4" class="mt-3 mt-md-0">
                                            <b-form-group>
                                                <label for="city" class="mb-2">Ciudad:</label>
                                                <b-form-input id="city" placeholder="Escriba su ciudad..."
                                                ></b-form-input>
                                            </b-form-group>
                                        </b-col>
                                    </b-row>
                                    <b-row>
                                        <b-col cols="12" md="4" class="mt-3">
                                            <b-form-group>
                                                <label for="street" class="mb-2">Calle:</label>
                                                <b-form-input id="street" placeholder="Escriba su calle..."
                                                ></b-form-input>
                                            </b-form-group>
                                        </b-col>
                                        <b-col cols="12" md="4" class="mt-3">
                                            <b-form-group>
                                                <label for="colony" class="mb-2">Colonia:</label>
                                                <b-form-input id="colony" placeholder="Escriba su colonia..."
                                                ></b-form-input>
                                            </b-form-group>
                                        </b-col>
                                        <b-col cols="12" md="4" class="mt-3">
                                            <b-form-group>
                                                <label for="postalcode" class="mb-2">Código postal:</label>
                                                <b-form-input id="postalcode" placeholder="Escriba su código postal..."
                                                ></b-form-input>
                                            </b-form-group>
                                        </b-col>
                                    </b-row>
                                    <b-row>
                                        <b-col cols="12" md="4" class="mt-3">
                                            <b-form-group>
                                                <label for="number1" class="mb-2">Número externo:</label>
                                                <b-form-input id="number1" placeholder="Escriba su número externo..."
                                                ></b-form-input>
                                            </b-form-group>
                                            <b-form-group>
                                                <label for="number2" class="mb-2 mt-3">Número interno:</label>
                                                <b-form-input id="number2"
                                                    placeholder="Escriba su número interno..."></b-form-input>
                                            </b-form-group>
                                        </b-col>
                                        <b-col cols="12" md="8" class="mt-3">
                                            <b-form-group>
                                                <label for="reference" class="mb-2">Referencia:</label>
                                                <b-form-textarea id="reference" placeholder="Escriba una referencia..."
                                                    rows="5"></b-form-textarea>
                                            </b-form-group>
                                        </b-col>
                                    </b-row>
                                </b-card-body>
                            </b-card>
                            <div class="mx-5 position-right">
                                <b-button type="submit" variant="primary" class="mx-4">Submit</b-button>
                                <b-button type="reset" variant="danger">Reset</b-button>
                            </div>
                        </b-form>
                    </b-card>
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>

<script>
export default {
    data() {
        return {
            form: {
                img: null,
                name: "",
                surname: "",
                lastname: "",
                birthdate: "",
                email: "",
                phone: "",
                country: "",
                state: "",
                city: "",
                street: "",
                colony: "",
                postalcode: "",
                number1: "",
                number2: "",
                reference: "",
            },
        }
    },
    methods: {
        showImg() {
            if (this.form.img) {
                return URL.createObjectURL(this.form.img)
            } else {
                return 'https://cdn-icons-png.flaticon.com/512/1160/1160358.png'
            }
        },
        onSubmit() {

            console.log(JSON.stringify(this.form))
        },
    },
}
</script>

<style scoped>
.img {
    width: 300px;
    height: 200px;
    object-fit: contain;
}
</style>