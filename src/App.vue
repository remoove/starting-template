<template>
  <div id="app">

    <app-header/>

    <div class="container">
      <h1 class="pt-3 pb-3">Персонажи Marvel</h1>

      <app-modal :character="character"/>
      <spinner v-if="loading"/> 

      <div class="row">
        <template v-for="(character, i) in characters">
          <div class="card mb-3 col-sm-12 col-md-6 col-lg-4">
            <div class="row gt-0">
              <div class="col-md-4">
                <img
                    :src="character.thumbnail"
                    class="img-fluid rounded-start"
                    :alt="character.name"
                    style="max-width: 100%"
                >
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">{{ character.name }}</h5>
                  <button
                      type="button"
                      class="btn btn-secondary"
                      data-bs-toggle="modal"
                      data-bs-target="#exampleModal"
                      @click="characterIndex = i"
                  >
                    Подробнее
                  </button>
                </div>
              </div>
            </div>
          </div>
        </template>
      </div>
    </div>
  </div>
</template>

<script>
import Spinner from "./components/Spinner";
import AppModal from "./components/AppModal";
import AppHeader from "./components/AppHeader";

export default {
  name: 'App',
  components: {
    AppHeader,
    AppModal,
    Spinner,
  },
  data() {
    return {
      loading: false,
      characters: [],
      characterIndex: 0,
    }
  },
  methods: {
    async getCharactersFromApi() {
      const url = 'https://netology-api-marvel.herokuapp.com/characters';

      return fetch(url)
          .then((res) => res.json())
          .then((json) => this.characters = json);
    }
  },
  computed: {
    character: function () {
      return this.characters[this.characterIndex] || null;
    }
  },
  async mounted() {
    this.loading = true;
    await this.getCharactersFromApi();
    this.loading = false;
  }
}
</script>

<style>

</style>
