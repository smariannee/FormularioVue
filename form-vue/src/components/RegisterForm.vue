<template>
    <div>
        <b-container fluid>
            <b-row>
                <b-col cols="12" class="p-3">
                    <b-card class="pt-3 pb-5 px-3">
                        <b-form @submit.prevent="onSubmit" @reset="cleanForm">
                            <b-card header-tag="header" class="mb-4">
                                <template #header>
                                    <h5 class="mb-0">Información personal</h5>
                                </template>
                                <b-card-body>
                                    <b-row>
                                        <b-col cols="12" md="4" align-self="center">
                                            <b-img :src="showImg()" class="img" alt="Imagen seleccionada" fluid rounded
                                                center></b-img>
                                            <b-form-group>
                                                <b-form-file class="mt-3" v-model="form.img" accept=".png"
                                                    @change="validateFile"></b-form-file>
                                                <b-form-invalid-feedback :state="errors.img" class="text-danger">
                                                    {{ messages.img }}
                                                </b-form-invalid-feedback>
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
                                                                    v-model="form.name"></b-form-input>
                                                                <b-form-invalid-feedback :state="errors.name"
                                                                    class="text-danger">
                                                                    {{ messages.name }}
                                                                </b-form-invalid-feedback>
                                                            </b-form-group>
                                                        </b-col>
                                                        <b-col cols="12" md="6" class="mt-3 mt-md-0">
                                                            <b-form-group>
                                                                <label for="surname" class="mb-2">Apellido paterno:</label>
                                                                <b-form-input id="surname"
                                                                    placeholder="Escriba su apellido paterno..."
                                                                    v-model="form.surname"></b-form-input>
                                                                <b-form-invalid-feedback :state="errors.surname"
                                                                    class="text-danger">
                                                                    {{ messages.surname }}
                                                                </b-form-invalid-feedback>
                                                            </b-form-group>
                                                        </b-col>
                                                    </b-row>
                                                    <b-row class="pb-4">
                                                        <b-col cols="12" md="6" class="mt-3">
                                                            <b-form-group>
                                                                <label for="lastname" class="mb-2">Apellido materno:</label>
                                                                <b-form-input id="lastname"
                                                                    placeholder="Escriba su apellido materno..."
                                                                    v-model="form.lastname"></b-form-input>
                                                                <b-form-invalid-feedback :state="errors.lastname"
                                                                    class="text-danger">
                                                                    {{ messages.lastname }}
                                                                </b-form-invalid-feedback>
                                                            </b-form-group>
                                                        </b-col>
                                                        <b-col cols="12" md="6" class="mt-3">
                                                            <b-form-group>
                                                                <label for="birthdate" class="mb-2">Fecha de
                                                                    nacimiento:</label>
                                                                <b-form-input id="birthdate" type="date"
                                                                    v-model="form.birthdate"></b-form-input>
                                                                <b-form-invalid-feedback :state="errors.birthdate"
                                                                    class="text-danger">
                                                                    {{ messages.birthdate }}
                                                                </b-form-invalid-feedback>
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
                                                                    v-model="form.email"></b-form-input>
                                                                <b-form-invalid-feedback :state="errors.email"
                                                                    class="text-danger">
                                                                    {{ messages.email }}
                                                                </b-form-invalid-feedback>
                                                            </b-form-group>
                                                        </b-col>
                                                        <b-col cols="12" md="6" class="mt-3">
                                                            <b-form-group>
                                                                <label for="birthdate" class="mb-2">Teléfono:</label>
                                                                <b-form-input id="birthdate" type="tel"
                                                                    placeholder="Escriba su número de teléfono..."
                                                                    v-model="form.phone"></b-form-input>
                                                                <b-form-invalid-feedback :state="errors.phone"
                                                                    class="text-danger">
                                                                    {{ messages.phone }}
                                                                </b-form-invalid-feedback>
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
                                        <b-col cols="12" md="6" class="mt-3 mt-md-0">
                                            <b-form-group>
                                                <label for="city" class="mb-2">Ciudad:</label>
                                                <b-form-input id="city" placeholder="Escriba su ciudad..."
                                                    v-model="form.city"></b-form-input>
                                                <b-form-invalid-feedback :state="errors.city" class="text-danger">
                                                    {{ messages.city }}
                                                </b-form-invalid-feedback>
                                            </b-form-group>
                                        </b-col>
                                        <b-col cols="12" md="6" class="mt-3 mt-md-0">
                                            <b-form-group>
                                                <label for="street" class="mb-2">Calle:</label>
                                                <b-form-input id="street" placeholder="Escriba su calle..."
                                                    v-model="form.street"></b-form-input>
                                                <b-form-invalid-feedback :state="errors.street" class="text-danger">
                                                    {{ messages.street }}
                                                </b-form-invalid-feedback>
                                            </b-form-group>
                                        </b-col>
                                    </b-row>
                                    <b-row>
                                        <b-col cols="12" md="6" class="mt-3">
                                            <b-form-group>
                                                <label for="postalcode" class="mb-2">Código postal:</label>
                                                <b-form-input id="postalcode" placeholder="Escriba su código postal..."
                                                    v-model="form.postalcode"></b-form-input>
                                                <b-form-invalid-feedback :state="errors.postalcode" class="text-danger">
                                                    {{ messages.postalcode }}
                                                </b-form-invalid-feedback>
                                            </b-form-group>
                                        </b-col>
                                        <b-col cols="12" md="6" class="mt-3">
                                            <b-form-group>
                                                <label for="number" class="mb-2">Número externo:</label>
                                                <b-form-input id="number" placeholder="Escriba su número externo..."
                                                    v-model="form.number"></b-form-input>
                                                <b-form-invalid-feedback :state="errors.number" class="text-danger">
                                                    {{ messages.number }}
                                                </b-form-invalid-feedback>
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
                city: "",
                street: "",
                postalcode: "",
                number: ""
            },

            messages: {
                img: "",
                name: "",
                surname: "",
                lastname: "",
                birthdate: "",
                email: "",
                phone: "",
                city: "",
                street: "",
                postalcode: "",
                number: ""
            },

            errors: {
                img: true,
                name: true,
                surname: true,
                lastname: true,
                birthdate: true,
                email: true,
                phone: true,
                city: true,
                street: true,
                postalcode: true,
                number: true
            },

            regex: {
                name: /^[a-zA-Z\s]*$/,
                email: /^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$/,
                number: /^[0-9]*$/,
            },
        }
    },

    methods: {
        showImg() {
            if (this.form.img) return URL.createObjectURL(this.form.img)
            return "https://cdn-icons-png.flaticon.com/512/1160/1160358.png"
        },

        validateRequired(field) {
            if (this.form[field]) {
                this.errors[field] = true
                this.messages[field] = ""
                return true
            } else {
                this.errors[field] = false
                this.messages[field] = "Campo obligatorio"
                return false
            }
        },

        validateLength(field, min, max) {
            if (this.form[field].length >= min && this.form[field].length <= max) {
                this.errors[field] = true
                this.messages[field] = ""
                return true
            } else {
                this.errors[field] = false
                if (min == max) this.messages[field] = `El campo debe tener ${min} caracteres`
                else
                    this.messages[field] = `El campo debe tener entre ${min} y ${max} caracteres`
                return false
            }
        },

        validateRegex(field, regex) {
            if (regex.test(this.form[field])) {
                this.errors[field] = true
                this.messages[field] = ""
                return true
            } else {
                this.errors[field] = false
                this.messages[field] = "Formato incorrecto"
                return false
            }
        },

        validateBirthdate(birthdate) {
            let today = new Date()
            let birth = new Date(birthdate)
            if (today > birth) {
                let age = today.getFullYear() - birth.getFullYear()
                let month = today.getMonth() - birth.getMonth()
                if (month < 0 || (month === 0 && today.getDate() < birth.getDate())) {
                    age--
                }
                if (age < 18) {
                    this.errors.birthdate = false
                    this.messages.birthdate = "Debes ser mayor de edad"
                    return false
                } else {
                    this.errors.birthdate = true
                    this.messages.birthdate = ""
                    return true
                }
            } else {
                this.errors.birthdate = false
                this.messages.birthdate = "Fecha inválida"
                return false
            }
        },

        validateFile(event) {
            const file = event.target.files[0];
            const size = file.size;
            console.log(file.size)
            if (size > 3000000) {
                this.errors.img = false
                this.messages.img = "La imagen debe pesar menos de 3MB"
                this.form.img = null
            }
        },

        onSubmit() {
            let validImg = false, validName = false, validSurname = false, validLastname = false, validBirthdate = false, validEmail = false, validPhone = false, validCity = false, validStreet = false, validPostalcode = false, validNumber = false
            if (this.validateRequired("img")) {
                validImg = true
            }
            if (this.validateRequired("name")) {
                if (this.validateLength("name", 3, 50)) {
                    if (this.validateRegex("name", this.regex.name)) {
                        validName = true
                    }
                }
            }
            if (this.validateRequired("surname")) {
                if (this.validateLength("surname", 3, 50)) {
                    if (this.validateRegex("surname", this.regex.name)) {
                        validSurname = true
                    }
                }
            }
            if (this.form.lastname) {
                if (this.validateLength("lastname", 3, 50)) {
                    if (this.validateRegex("lastname", this.regex.name)) {
                        validLastname = true
                    }
                }
            }
            if (this.validateRequired("birthdate")) {
                if (this.validateBirthdate(this.form.birthdate)) {
                    validBirthdate = true
                }
            }
            if (this.validateRequired("email")) {
                if (this.validateRegex("email", this.regex.email)) {
                    validEmail = true
                }
            }
            if (this.validateRequired("phone")) {
                if (this.validateLength("phone", 10, 10)) {
                    if (this.validateRegex("phone", this.regex.number)) {
                        validPhone = true
                    }
                }
            }
            this.validateRequired("city")
            this.validateRequired("street")
            if (this.validateRequired("postalcode")) {
                if (this.validateLength("postalcode", 5, 5)) {
                    if (this.validateRegex("postalcode", this.regex.number)) {
                        validPostalcode = true
                    }
                }
            }
            if (this.validateRequired("number")) {
                if (this.validateLength("number", 1, 5)) {
                    if (this.validateRegex("number", this.regex.number)) {
                        validNumber = true
                    }
                }
            }
            if (validImg && validName && validSurname && validLastname && validBirthdate && validEmail && validPhone && validPostalcode && validNumber) {
                alert("Formulario válido")
                this.cleanForm()
            }
        },

        resetValidation() {
            this.errors = {
                img: true,
                name: true,
                surname: true,
                lastname: true,
                birthdate: true,
                email: true,
                phone: true,
                city: true,
                street: true,
                postalcode: true,
                number: true
            }
        },

        resetMessages() {
            this.messages = {
                img: "",
                name: "",
                surname: "",
                lastname: "",
                birthdate: "",
                email: "",
                phone: "",
                city: "",
                street: "",
                postalcode: "",
                number: ""
            }
        },

        cleanForm() {
            this.form = {
                img: null,
                name: "",
                surname: "",
                lastname: "",
                birthdate: "",
                email: "",
                phone: "",
                city: "",
                street: "",
                postalcode: "",
                number: ""
            }
            this.resetValidation()
            this.resetMessages()
        }
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