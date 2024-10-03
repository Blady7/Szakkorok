<template>
  <main class="my-container">
    <h1 class="sticky-top">Diákok és a Szakkörök</h1>
    <div class="row">
      <div class="col-5">
        <!-- Diákok táblázat -->
        <table class="table">
          <thead>
            <tr>
              <th scope="col">Diákok</th>
              <th scope="col">Osztályok</th>
              <th scope="col">Szakkörök</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="tanulo in sortedTanulok" :key="tanulo.id">
              <td class="my-td">{{ tanulo.nev }}</td>
              <td class="my-td">{{ tanulo.osztaly }}</td>
              <td>
                <select
                  class="form-select"
                  v-model="tanulo.szakkorId"        
                >
                  <option
                    v-for="szakkor in szakkorok"
                    :key="szakkor.id"
                    :value="szakkor.id"
                  >
                    {{ szakkor.nev }}
                  </option>
                </select>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="col-7 px-5">
        <div class="sticky-top">
          <!-- Szakkörök -->
          <h2>Szakkörök</h2>
          <Szakkorok
            v-for="szakkor in szakkorok"
            :key="szakkor.id"
            :szakkor="szakkor"
            :tanulok="tanulok"
          />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import Szakkorok from "@/components/Szakkorok.vue";
export default {
  components: {
    Szakkorok
  },
  data() {
    return {
      tanulok: [
        { id: 1, nev: "Kovács Péter", osztaly: "9.A", szakkorId: 4 },
        { id: 2, nev: "Szabó Juli", osztaly: "10.B", szakkorId: 4 },
        { id: 3, nev: "Tóth Gábor", osztaly: "11.C", szakkorId: 4 },
        { id: 4, nev: "Tóth Katalin", osztaly: "9.A", szakkorId: 4 },
        { id: 5, nev: "Zsigmond Tamás", osztaly: "10.B", szakkorId: 4 },
        { id: 6, nev: "Horváth Zoltán", osztaly: "11.C", szakkorId: 4 },
        { id: 7, nev: "Balogh Bálint", osztaly: "10.B", szakkorId: 4 },
        { id: 8, nev: "Molnár Ádám", osztaly: "9.A", szakkorId: 4 },
        { id: 9, nev: "Nagy László", osztaly: "10.B", szakkorId: 4 },
        { id: 10, nev: "Papp Attila", osztaly: "11.C", szakkorId: 4 },
      ],
      szakkorok: [
        { id: 1, nev: "Tollaslabda" },
        { id: 2, nev: "Lábtoll-labda" },
        { id: 3, nev: "Röplabda" },
        { id: 4, nev: "Nem jár szakkörre" },
      ],
      szakkorTanulok: {
        Tollaslabda: [],
        Lábtolllabda: [],
        Röplabda: [],
      },
    };
  },
  computed: {
    sortedTanulok() {
      return this.tanulok.sort((a, b) => a.nev.localeCompare(b.nev));
    },
  },
};
</script>

<style>
.my-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f8f9fa;
}

h1 {
  font-size: 2.5rem;
  font-weight: 700;
  color: #343a40;
  margin-bottom: 20px;
  background-color: #007bff;
  color: rgb(255, 255, 255);
  padding: 10px;
  border-radius: 8px;
}

h2 {
  font-size: 2rem;
  font-weight: 600;
  color: #495057;
  margin-bottom: 15px;
  text-align: center;
}

.table {
  background-color: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.table thead {
  background-color: #007bff;
  color: white;
}

.my-td {
  padding: 10px;
  text-align: center;
  vertical-align: middle;
}

.select {
  width: 100%;
  padding: 10px;
  border-radius: 5px;
  border: 1px solid #ced4da;
}

.sticky-top {
  position: sticky;
  top: 0;
  background-color: #f8f9fa;
  z-index: 1000;
  padding: 10px;
}

.px-5 {
  padding-left: 3rem;
  padding-right: 3rem;
}

/* Hover effects */
.table tbody tr:hover {
  background-color: #e9ecef;
  cursor: pointer;
}

.form-select {
  border-radius: 5px;
  padding: 5px;
  background-color: #f1f1f1;
  border: 1px solid #ced4da;
  width: 100%;
}

/* Mobile responsive adjustments */
@media (max-width: 768px) {
  .my-container {
    padding: 10px;
  }

  h1 {
    font-size: 2rem;
  }

  h2 {
    font-size: 1.5rem;
  }

  .col-5, .col-7 {
    width: 100%;
  }
}
</style>

