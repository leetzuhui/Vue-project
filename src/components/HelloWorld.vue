<template>
  <div v-if="show">
    <div class="modal title" ref="title">Normal message</div>
    <div class="modal msg" ref="msg">Message from Modal: {{ msg }}</div>
  </div>
  <button @click="clickHandler">Click Me to show what the ref is</button>
  <br />
  <button @click="show = true">Show</button>
  <button @click="show = false">Hide</button>
  <button @click="show = !show">Toggle Show / Hide</button>
  <br />
  <div class="box-wrapper">
    <div class="box" :class="{ active: info[0].active }" @mouseenter.self="EventHandler"
      @mousedown.left="LeftClickToReset(0, $event)">
      MouseEnter
      <span class="info" v-if="info[0].text != ''">{{ info[0].text }}</span>
    </div>
    <div class="box" :class="{ active: info[1].active }" @mouseleave.self="EventHandler"
      @mousedown.left="LeftClickToReset(1)">
      MouseLeave
      <span class="info" v-if="info[1].text != ''">{{ info[1].text }}</span>
    </div>
    <div class="box" :class="{ active: info[2].active }" @dblclick.self="EventHandler"
      @mousedown.left="LeftClickToReset(2)">
      DoubleClick
      <span class="info" v-if="info[2].text != ''">{{ info[2].text }}</span>
    </div>
    <div class="box" :class="{ active: info[3].active }" @mousemove.self="EventMouseMoveHandler"
      @mousedown.left="LeftClickToReset(3)">
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
    msg: String
  },
  data() {
    return {
      show: true,
      info: [{ text: '', key: 0, active: false },
      { text: '', key: 0, active: false },
      { text: '', key: 0, active: false },
      { text: '', active: false }],
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
      if (event.type == 'mouseenter') {
        this.info[0].key++
        this.info[0].active = true
        this.info[0].text = 'mouseenter ' + (this.info[0].key == 1 ? '' : this.info[0].key)
      }
      else if (event.type == 'mouseleave') {
        this.info[1].key++
        this.info[1].active = true
        this.info[1].text = 'mouseleave ' + (this.info[1].key == 1 ? '' : this.info[1].key)
      }
      else if (event.type == 'dblclick') {
        this.info[2].key++
        this.info[2].active = true
        this.info[2].text = 'dblclick ' + (this.info[2].key == 1 ? '' : this.info[2].key)
      }
    },
    EventMouseMoveHandler(event) {
      this.info[3].active = true
      this.info[3].text = 'offsetX: ' + event.offsetX + ', offsetY: ' + event.offsetY
    },
    // click left button to remove the 'active' class
    LeftClickToReset(index) {
      this.info[index].active = false
    }
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
    transition: all 1s cubic-bezier(0.23, 1, 0.320, 1);

    .info {
      display: block;
      margin-top: 15px;
      font-size: 15px;
      font-weight: 200;
    }
  }

  .active {
    transition: all 1s cubic-bezier(0.23, 1, 0.320, 1);
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
