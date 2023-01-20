<template>
  <!-- @keyup.delete="$emit('backspace-key-click')" -->
  <Grid />
  <Keyboard 
    @key-click="addKey" 
    @enter-key-click="checkWord"
    @backspace-key-click="removeKey" />
</template>

<script>
import Grid from './components/Grid.vue'
import Keyboard from './components/Keyboard.vue'
import words from './words.js'

export default {
  components: {
    Grid,
    Keyboard,
  },
  data() {
    return {
      turns: 7,
      letterCount: 0,
      answer: [],
      grid: [],
      guess: [],
    }
  },
  /**
   * TODO:
   * 
   * bind delete key to removeKey function - DONE
   * 
   * if letter already exists remove it so that it
   * only shows green
   * 
   * remove keys that have already been checked
   * 
   * setup dictionary API 
   * 
   * checkWord must make sure the input is an
   * actual word using the dictionary API
   * 
   * answer must be a random 5 letter word grabbed
   * from dictionary API
   * 
   * created() { // used to fetch api data on load }
   */
  mounted() {
    // set answer to random word in words.js
    // this.answer = words[Math.floor(Math.random() * words.length)]
    this.answer = 'water'

    window.addEventListener('keydown', this.trggerKey)
  },
  destroyed() {
    window.removeEventListener('keydown', this.trggerKey)
  },
  methods: {
    trggerKey(e) {
      if (!e.metaKey && !e.shiftKey) {
        let key = e.key 
        if (e.code.includes('Key')) {
          this.addKey(key) 
        } else if (key === 'Backspace') {
          this.removeKey()
        } else if (key == 'Enter') {
          this.checkWord()
        }
      }
    },
    addKey(key) {
      if (this.letterCount < 5) {
        // console.log(`Key: ${key}`)

        let nextBox = document.querySelector(".grid-row__item[data-state='empty']")
        this.grid.push(nextBox)

        this.letterCount += 1

        nextBox.innerHTML = key
        this.guess.push(nextBox.innerHTML)
        nextBox.setAttribute("data-state", "tbd")
      }
    },
    removeKey() {
      if (this.grid.length) {
        let last = this.grid[this.grid.length - 1]

        this.letterCount -= 1

        this.grid.pop()
        this.guess.pop()
        last.innerHTML = ''
        last.setAttribute("data-state", "empty")
      }
    },
    checkWord() {
      /**
       * https://www.freecodecamp.org/news/build-a-wordle-clone-in-javascript/
       * 
       * check for correct letters first
       * if any letters aren't correct,
       * check if the exist in the array
       * else
       * set to not included
       */ 
      let answer = Array.from(this.answer)
      let guess = this.guess
      let guessString = this.guess.join('')

      if (!this.letterCount === 5) {
        alert('not enough letters')
        return
      }

      if (!words.includes(guessString)) {
        alert('not a valid word')
        return
      }

      for (let i = 0; i<guess.length; i++) {

        let state = ''
        let letter = guess[i]
        let letterPos = answer.indexOf(guess[i])

        // console.log(`Letter: ${letter}`)
        // console.log(`Letter Position: ${letterPos}`)

        if (letterPos === -1) {
          // if letter does not exist in word
          state = 'nomatch'
        } else {
          if (guess[i] === answer[i]) {
            // if guess letter pos and and answer letter
            // pos are the same
            state = 'correct'
          } else {
            // if guess letter is present in answer
            state = 'present'
          }

          guess[letterPos] = "#"
        }

        let delay = 200 * i
        setTimeout(()=> {
          // this.checkKey(letter, state)
          this.grid[i].setAttribute("data-state", state)
        }, delay)

      }

      if (guessString == this.answer) {
        alert('woo')
        this.turns = 0
        return
      } else {
        this.turns -= 1
        this.letterCount = 0
        this.guess = []

        if (this.turns == 0) {
          alert('You have run out of turns')
        }
      }

    },
    // checkKey(key, state) {
    //   let keys = Array.from(document.querySelectorAll('button'))
    //   keys.forEach((x) => {
    //     if (x == key) {
    //       key.setAttribute("data-state", state)
    //     }
    //   })
    // },
  },
}
</script>

<style lang="scss">
@import './assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  font-weight: normal;
}
</style>
