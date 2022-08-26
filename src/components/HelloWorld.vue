<template>
  <div v-if="show">
    <div class="modal title" ref="title">From Modal</div>
    <div class="modal msg" ref="msg">{{ msg }}</div>
  </div>
  <button @click="clickHandler">Click Me to show what the ref is</button>
  <br />
  <button @click="show = true">Show</button>
  <button @click="show = false">Hide</button>
  <button @click="show = !show">Toggle Show / Hide</button>
  <br />
  <div class="box-wrapper">
    <div class="box" :class="{ active: (info[0].text != '') }" @mouseover.self="EventHandler">
      Mouseover (Enter)
      <span class="info" v-if="info[0].text != ''">{{ info[0].text }}</span>
    </div>
    <div class="box" :class="{ active: (info[1].text != '') }" @mouseleave.self="EventHandler">
      MouseLeave
      <span class="info" v-if="info[1].text != ''">{{ info[1].text }}</span>
    </div>
    <div class="box" :class="{ active: (info[2].text != '') }" @dblclick.self="EventHandler">
      DoubleClick
      <span class="info" v-if="info[2].text != ''">{{ info[2].text }}</span>
    </div>
    <div class="box" :class="{ active: (info[3].text != '') }" @mousemove.self="EventHandler">
      MouseMove - See the X, Y value
      <span class="info" v-if="info[3].text != ''">{{ info[3].text }}</span>
    </div>
  </div>
  <br />
  <div class="book-list-wrapper">
    <h2>Book List:</h2>
    <ul class="book-list">
      <li v-for="item in books" :key="item.key">
        <p><b>{{ item.name }}</b> ({{ item.year }}) by <i>{{ item.author }}</i></p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      show: true,
      info: [{ text: '', key: 0 },
      { text: '', key: 0 },
      { text: '', key: 0 },
      { text: '' }],
      books: [
        { name: 'Divine Songs', year: 1715, author: 'Isaac Watts', key: 1 },
        { name: 'The Gigantick History of the Two Famous Giants', year: 1730, author: 'Thomas Boreman', key: 2 },
        { name: 'A Little Pretty Pocket', year: 1744, author: 'John Newbery', key: 3 },
        { name: 'A Description of Three Hundred Animals', year: 1730, author: 'Thomas Boreman', key: 4 },
        { name: 'The Governess, or The Little Female Academy', year: 1749, author: 'Sarah Fielding', key: 5 },
        { name: 'The Parables of Our Lord and Saviour Jesus Chris', year: 1768, author: 'Christopher Smart', key: 6 }
      ]
    };
  },
  methods: {
    clickHandler() {
      if (this.$refs.title)
        console.log(this.$refs.title);

      if (this.$refs.msg)
        console.log(this.$refs.msg);
    },
    EventHandler(event) {
      if (event.type == 'mouseover') {
        this.info[0].key++
        this.info[0].text = 'mouseover ' + (this.info[0].key == 1 ? '' : this.info[0].key)
      }
      else if (event.type == 'mouseleave') {
        this.info[1].key++
        this.info[1].text = 'mouseleave ' + (this.info[1].key == 1 ? '' : this.info[1].key)
      }
      else if (event.type == 'dblclick') {
        this.info[2].key++
        this.info[2].text = 'dblclick ' + (this.info[2].key == 1 ? '' : this.info[2].key)
      }
      else if (event.type == 'mousemove') {
        this.info[3].text = 'offsetX: ' + event.offsetX + ', offsetY: ' + event.offsetY;
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.modal {
  font-size: 25px;
  color: #25c141;
}

.box-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  user-select: none;
  -webkit-user-select: none;
  -moz-user-select: none;

  .box {
    max-width: 700px;
    min-width: 700px;
    max-height: 350px;
    margin: 50px auto;
    padding: 150px 200px;
    background-color: burlywood;
    border-radius: 30px;
    text-align: center;
    font-size: 30px;

    .info {
      display: block;
      margin-top: 15px;
      font-size: 15px;
      font-weight: 200;
    }
  }

  .active {
    background-color: crimson;
  }
}

.book-list-wrapper {
  text-align: left;
  font-size: 2.0rem;

  .book-list {
    font-size: 1.2rem;
  }
}
</style>
