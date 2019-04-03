<template>
  <div>
    <div>
      <div class="container" style="padding-left: 5%;padding-right: 5%">
        <div class="column">
          <label class="subtitle" style="">Search</label>
        </div>
        <div class="field">
          <input class="input" v-model="algoliaResults.name"/>
        </div>
        <div class="container">
          <div class="columns is-mobile is-multiline is-centered">
            <div class="column is-narrow" v-for="card in algoliaResults.data" :key="card.id">
              <figure class="image" style="width: 111px;height: 155px">
                <img :src="cardImage(card)">
              </figure>
            </div>
          </div>
        </div>
      </div>
      <br>
    </div>
  </div>
</template>
<script>
  import algoliasearch from 'algoliasearch'

  export default {
    data() {
      return {
        algoliaResults: {
          data: [],
          name: ''
        }
      }
    },
    methods: {
      cardImage(card) {
        return 'http://gatherer.wizards.com/Handlers/Image.ashx?multiverseid=' + card.multiverseid + '&type=card'
      }
    },
    watch: {
      'algoliaResults.name': function () {}
    }
  }
</script>