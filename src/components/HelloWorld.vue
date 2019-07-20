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
          src: 'data:image/jpeg;base64,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',
          title: 'Abelia',
          content: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam.',
        },
        {
          src: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTyj7x-LZMI6Gb-kZsbFVsRD5tZsqepp_PdqrX0PEnRINeFqyEW',
          title: 'Briar',
          content: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam.',
        },
        {
          src: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQIZ-SzURl3KBdZPZTKhz2_suOJqTsm9wnfybOstuo_vt7MQSmhvA',
          title: 'Colombine',
          content: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam.',
        },
        {
          src: 'https://res.cloudinary.com/bloomnation/c_limit,d_vendor:global:catalog:product:image.png,f_auto,fl_preserve_transparency,q_auto,w_1005/v1559888424/vendor/6762/catalog/product/2/0/20180822084802_file_5b7dcc02e4b91.jpg',
          title: 'Title',
          content: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam.',
        },
        {
          src: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRQfJBn6cE6NxDKz5sML6ixzMnzKzuLES9xHjelYQWtKRw68SX1',
          title: 'Acantha',
          content: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam. Lorem ipsum dolor sit amet, consectetur adipisicing elit.\n' +
            '       Accusamus aperiam cumque excepturi, in incidunt itaque officiis vel?\n' +
            '       Ad dicta et magni necessitatibus optio, qui quibusdam quidem ratione soluta,\n' +
            '       suscipit veniam.',
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
    width:500px;
    height:500px;
    border: 1px solid #152C55;
    border-radius: 10px;
  }
  h1{
    margin: 100px;
  }

</style>
