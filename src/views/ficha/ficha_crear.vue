<template>
    <div class="row">
        <div class="col-md-12">
            <div class="card">
                <div class="card-body">
                    <h1 class="text-center">FICHA PERSONAL</h1>
                    <div class="row">
                        <div class="col-md-4">
                            <img src="../../../heberlen.jpg.jpg" alt="" width="55%">
                        </div>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">nombre</label>
                        <input v-model="ficha.nombre" type="text" class="form-control">
                    </div>
                    <div class="row">
                        <div class="col-md-3">
                            <label class="form-label">ruc</label>
                            <input v-model="ficha.ruc" type="text" class="form-control">
                        </div>
                        <div class="col-md-3">
                            <div class="mb-3">
                                <label class="form-label">edad</label>
                                <input v-model="ficha.edad" type="text" class="form-control">
                            </div>

                        </div>
                        <div class="col-md-3">
                            <div class="mb-3">
                                <label class="form-label">fecha de nacimiento</label>
                                <input v-model="ficha.fechadenacimiento" type="text" class="form-control">
                            </div>
                        </div>
                        <div class="col-md-3">
                            <div class="mb-3">
                                <label class="form-label">direccion</label>
                                <input v-model="ficha.direccion" type="text" class="form-control">
                            </div>
                        </div>
                        <div class="col-md-6">
                            <div class="mb-3">
                                <label class="form-label">comuna</label>
                                <input v-model="ficha.comuna" type="text" class="form-control">
                            </div>
                        </div>
                        <div class="col-md-6">
                            <div class="mb-3">
                                <label class="form-label">fono</label>
                                <input v-model="ficha.fono" type="text" class="form-control">
                            </div>
                        </div>
                    </div>

                    <div class="mb-3">
                        <label class="form-label">gmail</label>
                        <input v-model="ficha.gmail" type="text" class="form-control">
                    </div>
                    <div class="row">
                        <div class="col-md-3">
                            <div class="mb-3">
                                <label class="form-label">colegio</label>
                                <input v-model="ficha.colegio" type="text" class="form-control">
                            </div>
                        </div>
                        <div class="col-md-3">
                            <div class="mb-3">
                                <label class="form-label">curso</label>
                                <input v-model="ficha.curso" type="text" class="form-control">
                            </div>
                        </div>
                        <div class="col-md-3">
                            <div class="mb-3">
                                <label class="form-label">religion</label>
                                <input v-model="ficha.religion" type="text" class="form-control">
                            </div>
                        </div>
                        <div class="col-md-3">
                            <div class="mb-3">
                                <label class="form-label">vive</label>
                                <input v-model="ficha.vive" type="text" class="form-control">
                            </div>
                        </div>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">nombre del padre</label>
                        <input v-model="ficha.nombredelpadre" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">profecion/ocupacion</label>
                        <input v-model="ficha.profecionocupacion" type="text" class="form-control">
                    </div>
                    <div class="row">
                        <div class="col-md-4">
                            <div class="mb-3">
                                <label class="form-label">casa</label>
                                <input v-model="ficha.casa" type="text" class="form-control">
                            </div>
                        </div>
                        <div class="col-md-4">
                            <div class="mb-3">
                                <label class="form-label">laboral</label>
                                <input v-model="ficha.laboral" type="text" class="form-control">
                            </div>
                        </div>
                        <div class="col-md-4">
                            <div class="mb-3">
                                <label class="form-label">celular</label>
                                <input v-model="ficha.celular" type="text" class="form-control">
                            </div>
                        </div>
                    </div>

                    <div class="mb-3">
                        <label class="form-label">nombre del madre</label>
                        <input v-model="ficha.nombredelmadre" type="text" class="form-control">
                    </div>
                    <div class="row">
                        <div class="col-md-4">
                            <div class="mb-3">
                                <label class="form-label">casa</label>
                                <input v-model="ficha.casa" type="text" class="form-control">
                            </div>
                        </div>
                        <div class="col-md-4">
                            <div class="mb-3">
                                <label class="form-label">laboral</label>
                                <input v-model="ficha.laboral" type="text" class="form-control">
                            </div>
                        </div>
                        <div class="col-md-4">
                            <div class="mb-3">
                                <label class="form-label">celular</label>
                                <input v-model="ficha.celular" type="text" class="form-control">
                            </div>
                        </div>
                    </div>

                </div>
            </div>
        </div>
        <div class="col-md-12">
            <button @click="guardar()" type="button" class="btn btn-primary">Guardar</button>
            <RouterLink class="btn btn-light" to="/curso_listar">Cancelar</RouterLink>
        </div>
    </div>
</template>
<script>

import { collection, getDocs, query, where, addDoc } from "firebase/firestore";
import { auth, db } from "../../firebaseConfig";
import { defineComponent } from 'vue';
export default defineComponent({
    // name: 'scanner',
    data() {
        return {
            loadingDoc: false,
            ficha: {
                nombre: '',
                ruc: '',
                edad: '',
                fechadenacimiento: '',
                direccion: '',
                comuna: '',
                fono: '',
                gmail: '',
                colegio: '',
                curso: '',
                vive: '',
                nombredelpadre: '',
                profecionocupacion: '',
                casa: '',
                laboral: '',
                celular: '',
                nombredelmadre: '',
                profecionocupacion: '',
                casa: '',
                laboral: '',
                celular: '',

            },
        }
    },
    methods: {
        async guardar() {
            try {
                const q = query(collection(db, 'ficha'));
                const docRef = await addDoc(q, this.ficha);
                this.$router.push({ name: 'ficha_listar' })
            } catch (error) {
                console.log(error);
            }
        },
    },
    created() {
    }
})
</script>