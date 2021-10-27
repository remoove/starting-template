<template>
  <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">{{ character.name }}</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <img style="max-width: 100%" :src="character.thumbnail"
               :alt="character.name">
          <div class="">
            <span class="text-muted">{{ character.modified }}</span>
            <h5 class="pt-3">Описание:</h5>
            <span>
              {{character.description}}
                        </span>

            <h5 class="pt-3">Комиксы:</h5>
            <ul v-for="(el, i) of character.comics">
              <li :key="i">{{el.name}}</li>
            </ul>
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Закрыть</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: "AppModal",
        props: ["character"]
    }
</script>

<style scoped>

</style>
