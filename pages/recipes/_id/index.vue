<template>
  <section class="single-recipe">
    <h1>{{ recipe.title }}</h1>
    <div>
      <img class="recipe-image" :src="recipe.thumbnail" :alt="recipe.title" />
    </div>
    <p>{{ recipe.descriptionText }}.</p>
  </section>
</template>

<script>
export default {
    //context is specific to asyncData(?)
  asyncData(context) {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve({
          //real world, you can do a fetch for the specific restaurant that would be pulled into here.
          //for this example we just used the same hard coded recipe list and will do a .filter on it to find what we are looking for based on the id
          recipe: [
            {
              id: "1",
              title: "Delicious Pizza",
              previewText: "Awesome Pizza",
              descriptionText: "This is really a delicious meal!",
              thumbnail:
                "https://www.bbcgoodfood.com/sites/default/files/recipe-collections/collection-image/2016/11/one-pot-paneer-curry-pie.jpg",
            },
            {
              id: "2",
              title: "Tasty Food",
              previewText: "Food so good",
              descriptionText: "This is really a delicious meal!",
              thumbnail:
                "https://hips.hearstapps.com/del.h-cdn.co/assets/18/06/1517928338-delish-mongolian-ramen-and-meatballs-still001.jpg",
            },
          ].find(el => el.id === context.params.id),
        });
      }, 1500);
    });
  },
};
</script>

<style scoped>
.recipe-image{
    width: 100%
}

.single-recipe {
  display: flex;
  justify-content: center;
  flex-flow: column;
  align-items: center;
  text-align: center;
  padding: 30px;
}
</style>