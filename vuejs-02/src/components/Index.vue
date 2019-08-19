<template>
  <div class="index container">
    <div class="card"
      v-for="recipe in recipies"
      :key="recipe.id">
      <div class="card-content">
        <i class="material-icons delete"
          @click="deleteRecipe(recipe.id)">delete</i>
        <h2 class="indigo-text">
          {{ recipe.title }}
          <ul class="keywords">
            <li v-for="(keyword, index) in recipe.keywords"
              :key="index">
              <span class="chip">{{ keyword }}</span>
            </li>
          </ul>
        </h2>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Index',
  data () {
    return {
      recipies: [
        {
          title: 'Symfony 4',
          slug: 'symfony-4',
          keywords: [
              'twig',
              'doctrine',
              'php'
          ],
          id: '1'
        },
        {
          title: 'Spring Framework',
          slug: 'spring-framework',
          keywords: [
              'java',
              'hibernate',
              'rmi'
          ],
          id: '2'
        }
      ]
    }
  },
    methods: {
      deleteRecipe(id) {
        this.recipies = this.recipies.filter(recipe => {
            return recipe.id != id
        })
      }
    }
}
</script>

<style>
  .index {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: 30px;
    margin-top: 60px;
  }
  .index h2 {
    font-size: 1.8em;
    text-align: center;
    margin-top: 0;
  }
  .index .keywords {
    margin: 30px auto;
  }
  .index .keywords li {
    display: inline-block;
  }
  .index .delete {
    position: absolute;
    top: 4px;
    right: 4px;
    cursor: pointer;
    color: #aaa;
    font-size: 1.4em;
  }
</style>
