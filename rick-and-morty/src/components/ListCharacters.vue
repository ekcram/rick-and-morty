<script>
import { onMounted, computed } from 'vue'
import {useStore} from 'vuex'

export default {
  setup(){
    const store = useStore()
    const characters = computed(()=>{
      return store.state.charactersFilter
    })

    onMounted(()=>{
      //dispatch se utiliza para acceder a las actions del store
      store.dispatch('getCharacters')
    })

    return {
      characters
    }
  }

}
</script>
<template>
  <section>
    <div class="characters">
      <div class="characters__item" v-for="character in characters" :key="character.id">
        {{ character.name }}
      </div>
    </div>
  </section>
</template>

<style lang="scss">

</style>