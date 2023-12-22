<template>
    <div class="row">
        <div class="col-md-12">
            <div class="card">
                <div class="card-body">
                    <h1 class="text-center">Rally de Clanes BJ 2008- Hjoa de registro</h1>
                    <h2 class="text-center">Datos Genertales</h2>
                    <div class="row">
                        <div class="col-md-4">
                            <img src="../../../heberlen.jpg.jpg" alt="" width="55%">
                        </div>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">nombre del equipo</label>
                        <input v-model="ficha.nombre" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">categoria</label>
                        <input v-model="ficha.categoria" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">provincia</label>
                        <input v-model="ficha.provincia" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">grupo</label>
                        <input v-model="ficha.grupo" type="tetx" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label"> de participantes</label>
                        <input v-model="ficha.participantes" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">telefono celular 1</label>
                        <input v-model="ficha.telefono1" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">telefono celular 2</label>
                        <input v-model="ficha.telefono2" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">modelo</label>
                        <input v-model="ficha.modelo" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">año</label>
                        <input v-model="ficha.año" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">placas</label>
                        <input v-model="ficha.placas" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">religion</label>
                        <input v-model="ficha.religion" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">llanta de refacion</label>
                        <input v-model="ficha.llanta" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">suguro</label>
                        <input v-model="ficha.seguro" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">herramiestas</label>
                        <input v-model="ficha.herramientas" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">luces en buen estado</label>
                        <input v-model="ficha.luces" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">cinturon de seguridad</label>
                        <input v-model="ficha.seguridad" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">nombre completo</label>
                        <input v-model="ficha.nombre" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">licencia</label>
                        <input v-model="ficha.licencia" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">edad</label>
                        <input v-model="ficha.edad" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">sexo</label>
                        <input v-model="ficha.sexo" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">cum</label>
                        <input v-model="cum" type="text" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">equipo</label>
                        <input v-model="equipo" type="text" class="form-control">
                    </div>
                </div>

            </div>
        </div>
    </div>
    <div class="col-md-12">
        <button @click="guardar()" type="button" class="btn btn-primary">Guardar</button>
        <RouterLink class="btn btn-light" to="/curso_listar">Cancelar</RouterLink>
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
                categoria: '',
                provincia: '',
                grupo: '',
                participantes: '',
                telefono1: '',
                telefono2: '',
                modelo: '',
                año: '',
                placas: '',
                relegion: '', 
                llanta: '', 
                seguro: '', 
                herramientas: '', 
                luces: '', 
                seguridad: '',
                nombre: '',
                licencia: '',
                edad: '',
                sexo: '', 
                cum: '',
                equyipo: '', 

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