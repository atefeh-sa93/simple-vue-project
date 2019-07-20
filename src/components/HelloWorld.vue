<template>
  <div>
  <div style="text-align: center">
    <input type="search" v-model="search" placeholder="search" class="input-form">
  </div>
  <template v-if="filteredBlog.length">
    <div class="row" id="blog" v-for="blog in filteredBlog">
      <div class="col-md-6">
        <img :src="blog.src">
      </div>
      <div class="col-md-6">
        <h3>{{ blog.title}}</h3>
        <p>{{ blog.content}}</p>
        <router></router>
      </div>
    </div>
  </template>
  <template v-else>
    <h1>No Result Found</h1>
  </template>
</div>
</template>

<script>
export default {
  name: 'HelloWorld',

  data() {
    return {
      blogs: [
        {
          src: 'https://images.unsplash.com/photo-1500479694472-551d1fb6258d?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80',
          title: 'Fox',
          content: 'The word fox comes from Old English, which derived from Proto-Germanic *fuhsaz.[nb 1] ' +
                  'This in turn derives from Proto-Indo-European *puḱ-, meaning ’thick-haired; tail’.[nb 2] ' +
                  'Male foxes are known as dogs, tods or reynards, females as vixens, and young as cubs, pups, ' +
                  'or kits, though the latter name is not to be confused with a distinct species called kit foxes. ' +
                  'Vixen is one of very few words in modern English that retains the Middle English southern dialect "v" ' +
                  'pronunciation instead of "f" (i.e. northern English "fox" versus southern English "vox").[3] A group of ' +
                  'foxes is referred to as a skulk, leash, or earth.[4][5]',
        },
        {
          src: 'https://images.unsplash.com/photo-1521651201144-634f700b36ef?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80',
          title: 'Elephant',
          content: 'Elephants are large mammals of the family Elephantidae in the order Proboscidea. Three species are currently recognised: the African ' +
                    'bush elephant (Loxodonta africana), the African forest elephant (L. cyclotis), and the Asian elephant (Elephas maximus). Elephants are ' +
                    'scattered throughout sub-Saharan Africa, South Asia, and Southeast Asia. Elephantidae is the only surviving family of the order Proboscidea; ' +
                    'other, now extinct, members of the order include deinotheres, gomphotheres, mastodons, anancids and stegodontids; Elephantidae itself also contains ' +
                    'several now extinct groups, such as the mammoths and straight-tusked elephants.',
        },
        {
          src: 'https://images.unsplash.com/photo-1484557985045-edf25e08da73?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1267&q=80',
          title: 'Sheep',
          content: 'Domestic sheep (Ovis aries) are quadrupedal, ruminant mammals typically ' +
            'kept as livestock. Like most ruminants, sheep are members of the order Artiodactyla, ' +
            'the even-toed ungulates. Although the name sheep applies to many species in the genus Ovis, ' +
            'in everyday usage it almost always refers to Ovis aries. Numbering a little over one billion, domestic ' +
            'sheep are also the most numerous species of sheep. An adult female sheep is referred to as a ewe (/juː/), ' +
            'an intact male as a ram or occasionally a tup, a castrated male as a wether, and a younger sheep as a lamb.',
        },
        {
          src: 'https://images.unsplash.com/photo-1505576652881-6b80543182f5?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60',
          title: 'Giraffe',
          content: 'The giraffe (Giraffa) is an African even-toed ungulate mammal, the tallest living terrestrial animal and ' +
                    'the largest ruminant. It is traditionally considered to be one species, Giraffa camelopardalis, with nine subspecies. ' +
                    'However the existance of up to eight extant giraffe species have been described, based upon research into the mitochondrial ' +
                    'and nuclear DNA, as well as morphological measurements of Giraffa. Seven other species are extinct, prehistoric species known from fossils.',
        },
        {
          src: 'https://images.unsplash.com/photo-1457410129867-5999af49daf7?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60',
          title: 'Cat',
          content: 'The cat (Felis catus) is a small carnivorous mammal.[1][2] It is the only domesticated species in the family Felidae ' +
                    'and often referred to as the domestic cat to distinguish it from wild members of the family.[4] The cat is either ' +
                    'a house cat or a farm cat, which are pets, or a feral cat, which ranges freely and avoids human contact.' +
                    'A house cat is valued by humans for companionship and for its ability to hunt rodents. About 60 cat breeds are recognized by various cat registries.[6]',
        },
      ],
      search: '',
    };
  },

  computed: {
    filteredBlog(){
      return this.blogs.filter((blog) => {
        return blog.title.toLowerCase().trim().match(this.search);
      });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .input-form{
    outline: none;
    border: 2px solid #152C55;
    border-radius: 20px;
    margin:10px;
    padding: 20px;
    box-shadow: 2px 5px 5px #7688A9;
  }
  #blog{
    margin: 10px;
    padding: 10px;
    background: #7688A9;
  }
  h3{
    font-weight: 700;
    margin: 10px;
  }
  p{
    font-size: 15px;
  }
  img{
    width: 500px;
    border: 1px solid #152C55;
    border-radius: 10px;
  }
  h1{
    margin: 100px;
  }

</style>
