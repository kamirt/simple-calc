<template>
  <main>
    <div class="container">
      <section class="calc">
        <div v-for="(division, idx) in divisions" class="cycle">
          <Division :division="division" v-model="divisions[idx]" />
          <Plus v-if="idx != divisions.length-1" />
        </div>
      </section>
      <aside class="equality-block">
        <Equals />
        <div class="sum">{{ this.result }}</div>
      </aside>
    </div>
    <button
      @click="addDivision"
      class="add-btn"
      :class="btnClass"
      :disabled="btnClass">Добавить дробь</button>
  </main>
</template>

<script>
import Division from "./components/Division";
import Plus from "./components/Plus";
import Equals from "./components/Equals";

export default {
  name: 'app',
  components: {
    Division,
    Plus,
    Equals
  },
  computed: {
    result () {
      let res = 0;
      const divs = this.divisions;
      for (let i in divs) {
        let div = divs[i];
        if (div.numerator && div.denominator) {
          res += (div.numerator / div.denominator);
        }
      }
      return res.toFixed(2); // прото для красоты
    }
  },
  data () {
    return {
      divisions: [
        {
          numerator: null,
          denominator: null
        },
        {
          numerator: null,
          denominator: null
        }
      ],
      btnClass: false
    }
  },
  mounted () {
    const division = '';
  },
  methods: {
    addDivision () {
      if (this.divisions.length > 5) {
        this.btnClass = 'add-btn_disabled';
        return;
      }
      this.divisions.push({
        up: 0,
        down: 1
      })
    }
  }
}
</script>

<style lang="scss" scoped>
  @import "assets/css/normalize.css";
  main {
    width: 90%;
    margin: auto;
  }
  .container {
    margin: auto;
    display: flex;
  }
  .calc {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
  }
  .cycle {
    flex-shrink: 1;
    display: flex;
    align-items: center;
  }
  .cycle:last-child {
    width: auto;
  }
  .sum {
    width: 50px;
    height: 50px;
    font-size: 2.6rem;
    margin-left: 20px;
  }
  .equality-block {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .add-btn {
    margin: 10px 10px;
    padding: 10px 20px;
    border: none;
    outline: none;
    border-radius: 3px;
    font-family: sans-serif;
    font-size: 1rem;
    color: white;
    background: #31a7fb;
    box-shadow: 1px 1px 2px 0px #9e9e9e;
    &:hover {
      box-shadow: 1px 1px 8px 0px #9e9e9e;
    }
    &:active {
      box-shadow: 0px 0px 2px 0px #9e9e9e;
    }
    &_disabled {
      background: grey;
      box-shadow: none;
    }
  }
  @media screen and (max-width: 768px) {
    .container {
      flex-direction: column;
    }
    .cycle {
      width: calc(100% * (1/2) - 1px);
    }
  }

</style>
