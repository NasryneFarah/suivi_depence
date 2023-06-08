<script>
import Detail from "./components/Detail.vue";
export default {
  data() {
    return {
      showDetail: "",
      budget: [
        {
          montant: 200000,
          description: "L'argent du paiya",
          date: Date.now(),
        },

        {
          montant: 100000,
          description: "La scolarité",
          date: Date.now(),
        },
      ],

      depences: [
        {
          montant: 20000,
          description: "transport",
          date: Date.now(),
        },

        {
          montant: 30000,
          description: "Boisson",
          date: Date.now(),
        },

        {
          montant: 200,
          description: "unité",
          date: Date.now(),
        },

        {
          montant: 5000,
          description: "Nourriture",
          date: Date.now(),
        },

        {
          montant: 10000,
          description: "tontine",
          date: Date.now(),
        },
      ],

      solde: [
        {
          montant: 200000,
          date: Date.now(),
        },

        {
          montant: -20000,
          date: Date.now(),
        },

        {
          montant: -30000,
          date: Date.now(),
        },

        {
          montant: -200,

          date: Date.now(),
        },

        {
          montant: -5000,

          date: Date.now(),
        },
        {
          montant: 100000,
          date: Date.now(),
        },
        {
          montant: -10000,

          date: Date.now(),
        },
      ],
    };
  },

  computed: {
    totalBudget() {
      let somme = 0;
      this.budget.map((budget) => {
        somme += budget.montant;
      });
      return somme;
    },

    totalDepence() {
      let somme = 0;
      this.depences.map((depence) => {
        somme += depence.montant;
      });
      return somme;
    },

    totalSolde() {
      let somme = 0;
      this.solde.map((solde) => {
        somme += solde.montant;
      });
      return somme;
    },
  },

  components: {
    Detail,
  },

  methods: {
    toggleDetail(detail) {
      if (this.showDetail == detail) {
        this.showDetail = "";
        console.log(this.showDetail);
      } else if (this.showDetail != "" && this.showDetail != detail) {
        this.showDetail = detail;
        console.log(this.showDetail);
      } else if (this.showDetail == "") {
        this.showDetail = detail;
      }
    },
  },
};
</script>

<template>
  <div class="container">
    <!--Partie de gauche-->
    <div class="wrapper">
      <div class="entree">
        <fieldset>
          <legend>Entrée d'argent</legend>
          <form action="#" method="post">
            <label for="number">Montant</label>
            <input type="number" />

            <label for="text">Description</label>
            <input type="text" />

            <div class="btn_entree">
              <button><i class="bi bi-download"></i> Enregister</button>
            </div>
          </form>
        </fieldset>
      </div>
      <br /><br />

      <div class="sortie">
        <fieldset>
          <legend>Sortie d'argent</legend>
          <form action="#" method="post">
            <label for="number">Montant</label>
            <input type="number" />

            <label for="text">Description</label>
            <input type="text" />

            <div class="btn_sortie">
              <button><i class="bi bi-download"></i> Enregister</button>
            </div>
          </form>
        </fieldset>
      </div>
    </div>

    <!--Partie de droite-->

    <div class="wrapper">
      <div class="resume">
        <div>
          <img src="img/budget.png" width="50" />
          <h3>Budget</h3>
          <h4>{{ totalBudget }}</h4>
          <button @click="toggleDetail('budget')">Détails</button>
        </div>
        <div>
          <img src="img/depen.png" width="50" alt="" />
          <h3>Dépense</h3>
          <h4>{{ totalDepence }}</h4>
          <button @click="toggleDetail('depense')">Détails</button>
        </div>
        <div>
          <img src="img/solde.png" width="50" alt="" />
          <h3>Solde</h3>
          <h4>{{ totalSolde }}</h4>
          <button @click="toggleDetail('solde')">Détails</button>
        </div>
      </div>
      <transition 
      enter-active-class="animate__animated animate__fadeInUpBig"
      leave-active-class="animate__animated animate__fadeOut"
      >
        <Detail  v-show="showDetail" />
      </transition>
    </div>
  </div>
</template>

<style>
body {
  height: 100vh;
  background-color: #fdf2e9;
  font-family: "Nunito Sans", sans-serif;
}

.container {
  display: flex;
}

.wrapper {
  width: 50%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 12%;
}

.entree,
.sortie,
.resume,
.details {
  width: 70%;
}
.entree fieldset {
  width: 60%;
  padding: 15px;
}

.entree form {
  display: flex;
  flex-direction: column;
}

.entree input {
  margin-top: 5px;
  margin-bottom: 5px;
  border-radius: 3px;
}

.btn_entree {
  margin-top: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn_entree button {
  padding: 8px 12px;
  border: none;
  border-radius: 5px;
  background-color: #edbb99;
  color: black;
  font-size: 16px;
  transition: all 0.5s ease;
  cursor: pointer;
}

.btn_entree button:hover {
  background-color: #dc7633;
  color: whitesmoke;
}

.sortie fieldset {
  width: 60%;
  padding: 15px;
}

.sortie form {
  display: flex;
  flex-direction: column;
}

.sortie input {
  margin-top: 5px;
  margin-bottom: 5px;
  border-radius: 3px;
}

.btn_sortie {
  margin-top: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn_sortie button {
  padding: 8px 12px;
  border: none;
  border-radius: 5px;
  background-color: #edbb99;
  color: black;
  font-size: 16px;
  transition: all 0.5s ease;
  cursor: pointer;
}

.btn_sortie button:hover {
  background-color: #dc7633;
  color: whitesmoke;
}

/*--Partie Droite--*/
.row {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.total {
  font-weight: bold;
  display: flex;
  text-align: right;
  align-items: center;
}
span {
  padding: 5px;
}

.resume {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 20px;
}

.resume button {
  padding: 8px 12px;
  border: none;
  border-radius: 5px;
  background-color: #edbb99;
  color: black;
  font-size: 16px;
  transition: all 0.5s ease;
  cursor: pointer;
}

.resume button:hover {
  background-color: #dc7633;
  color: whitesmoke;
}
</style>
