<template>
  <div class="container">

    <div id="app" class="general">
      <div class="bg-primary text-white text-center p-2  ">
        <h4><strong> {{dato1}} </strong></h4>
        <h5><strong>{{dato2}}</strong></h5>
      </div>
      <center>
        <hr width="80%" color="white">
      </center>
      <div class="container-fluid p-4">

        <p>Daily </p>

        <div class="row" v-for="t in  filtrotareas" v-bind:key="t.descripcion">

          <div class="col">{{t.descripcion}}</div>
          <div class="col-2">
            <input type="checkbox" v-model="t.terminado" class="form-check-input">
            {{t.terminado}}
          </div>

        </div>

      </div>



      <div class="row py-2">
        <div class="col">
          <input class="form-control" placeholder="Notes" required="Registre Note" v-model="nuevoItem">
        </div>
        <div class="col-2">

          <button class="btn btn-secondary " color="#8c004b" v-on:click="addtarea" width="100%"><i
              class="bi bi-plus-circle-fill"></i></button>
        </div>
      </div>

      <div class="row-bg-dark py-2 mts-2 text-white">
        <div class="col text-center">
          <input type="checkbox" class="form-check-input" v-model="banderasCompleta">
          <label class="form-check-label font-weight-bold">
            Ocultar las tareas completaa
          </label>
        </div>
      </div>

    </div>

  </div>

</template>

<script>


export default {
  data() {
    return {
      dato1: 'Daily UI todo List',
      dato2: 'practice design Everiday',
      tareas: [
        { descripcion: "Check Email", terminado: false },
        { descripcion: "Search for inspiration", terminado: false },
        { descripcion: "Design the task", terminado: false },
        { descripcion: "Post it on Social Media", terminado: false },
        { descripcion: "Get review and Update it", terminado: false }
      ],
      banderasCompleta: true,
      nuevoItem: ""
    }
  },
  computed: {
    filtrotareas() {
      return this.banderasCompleta ? this.tareas.filter(t => !t.terminado) : this.tareas;

    }
  },
  methods: {
    addtarea() {
      this.tareas.push(
        {
          descripcion: this.nuevoItem,
          terminado: false
        },
        this.nuevoItem = ""
      )

    }

  }
}
</script>

<style>
.container {

  height: 100vh;
  margin: 0%;
  padding: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-image:
    linear-gradient(rgb(117, 97, 202), rgb(206, 207, 100)4%);

}

.general {
  max-width: 480px;
  width: 100%;
  max-height: 100%;
  background-color: black;
  padding: 30px;
  border-radius: 25;
  overflow: auto;
  color: rgb(238, 217, 217);
}

.general h4,
h5 {
  display: block;
}
</style>