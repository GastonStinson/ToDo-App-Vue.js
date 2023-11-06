<template>
    <div class="container mt-5">
        <div class="row">
            <div class="col-lg-8 offset-lg-2">
                <input type="text" class="form-control form-control-lg" placeholder="Ingresar tarea..."
                    v-model="nombreTarea" v-on:keyup.enter=agregarTarea() />
                <br />
            </div>
        </div>
        <div class="row">
            <div class="col-lg-6 offset-lg-3">
                <div class="card p-2" v-if="tareas.length === 0">
                    <h6>No hay tareas para mostrar</h6>
                </div>
                <ul class="list-group ">
                    <li class="list-group-item d-flex justify-content-between" v-for="(tarea, index) in tareas"
                        v-bind:key="index">
                        <span class="cursor" @click="alternarEstado(index, tarea)">
                            <i class="fa-regular fa-circle" v-if="tarea.estado === false"></i>
                            <i class="fa-regular fa-check-circle" v-else></i>
                        </span>
                        <h5 v-bind:class="[tarea.estado ? 'completado' : '']">{{ tarea.nombre }}</h5>
                        <span class="cursor text-danger" @click="eliminarTarea(index)">
                            <i class="fa-solid fa-trash"></i>
                        </span>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            tareas: [],
            nombreTarea: ''
        }
    },
    methods: {
        agregarTarea() {
            this.tarea = {
                nombre: this.nombreTarea,
                estado: false
            }

            this.tareas.push(this.tarea);
            this.nombreTarea = '';
            console.log(this.tareas);
        },
        eliminarTarea(index) {
            this.tareas.splice(index, 1)
        },
        alternarEstado(index, tarea) {
            this.tareas[index].estado = !tarea.estado;

        }
    }
}
</script>

<style scoped>
input {
    text-align: center;
}

.form-control-lg {
    font-size: 1.6rem;
}

.cursor {
    cursor: pointer;
}

.completado {
    text-decoration: line-through;
}
</style>