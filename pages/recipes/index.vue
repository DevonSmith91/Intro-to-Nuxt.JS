<template>
    <section class="recipes">
        <Recipe 
            v-for="recipe in recipes"
            :key="recipe.id"
            :thumbnail="recipe.thumbnail"
            :title="recipe.title"
            :id="recipe.id"
            :previewText="recipe.previewText"
        />
    </section>
</template>


<script>
import Recipe from '@/components/Recipe'

export default {
    components: {
        Recipe
    },
    asyncData() {
            // real life use, do a fetch here to a DB and return a promise that can be used to populate the data that will be put into these recipes
            // return axios.get()
            return new Promise((resolve, reject)=>{
                setTimeout(()=>{
                    resolve({
                        recipes: [
                            {
                                id: "1",
                                title: "Delicious Pizza",
                                previewText: "Awesome Pizza",
                                thumbnail: "https://www.bbcgoodfood.com/sites/default/files/recipe-collections/collection-image/2016/11/one-pot-paneer-curry-pie.jpg"
                            },
                            {
                                id: "2",
                                title: "Tasty Food",
                                previewText: "Food so good",
                                thumbnail: "https://hips.hearstapps.com/del.h-cdn.co/assets/18/06/1517928338-delish-mongolian-ramen-and-meatballs-still001.jpg"
                            }
                        ]
                    })
                })
            })
    }
};
</script>


<style scoped>
.recipes {
    display: flex;
    flex-flow: row wrap;
    justify-content: center;
    align-items: center;
}
</style>