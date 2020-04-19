<template>
  <div id="app">
    <div>
      <b-container class="header mt-5">
        <b-row align-h="center">
          <b-col md="auto">
            <h1>RPG Баланс персонажей</h1>
          </b-col>
        </b-row>

        <b-row class="mt-5">
          <b-col>
            <h4>Базовые характеристики персонажа</h4>
            <ul>
              <li>Сила
                <ul>
                  <li>Здоровье</li>
                  <li>Удача</li>
                </ul>
              </li>

              <li>Ловкость
                <ul>
                  <li>Скорость</li>
                  <li>Точность</li>
                </ul>
              </li>

              <li>Интеллект
                <ul>
                  <li>Мана</li>
                  <li>Точность?</li>
                </ul>
              </li>

              <li>Выносливость
                <ul>
                  <li>Бодрость</li>
                </ul>
              </li>

            </ul>

            <h4>Характеристики персонажа</h4>
            <ul>
              <li>Урон
                <ul>
                  <li>Физический урон</li>
                  <li>Магический урон</li>
                </ul>
              </li>

              <li>Броня
                <ul>
                  <li>Защита от физического урона</li>
                  <li>Защита от магического урона</li>
                </ul>
              </li>
            </ul>

          </b-col>

          <b-col>
            <h4>Пример расчета</h4>

            <div class="mt-2 p-2 border">
              <label for="range-1">Сила</label>
              <b-form-input id="range-1" v-model="power" type="range" :min="1" :max="10" disabled="disabled"></b-form-input>
              <div class="mt-2">Сила: {{ power }}</div>
              <b-button-group class="mt-2">
                <b-button @click="toLowPower">Снизить</b-button>
                <b-button @click="toUpPower">Повысить</b-button>
              </b-button-group>
              <!-- <b-form-input v-model="power" placeholder="Power" @change="getPower"></b-form-input> -->
            </div>

            <div class="mt-2 p-2 border">
              <label for="range-2">Скорость</label>
              <b-form-input id="range-2" v-model="speed" type="range" :min="1" :max="10" disabled="disabled"></b-form-input>
              <div class="mt-2">Скорость: {{ speed }}</div>
              <b-button-group class="mt-2">
                <b-button @click="toLowSpeed">Снизить</b-button>
                <b-button @click="toUpSpeed">Повысить</b-button>
              </b-button-group>
              <!-- <b-form-input v-model="speed" placeholder="Speed"></b-form-input> -->

            </div>

          </b-col>
        </b-row>
      </b-container>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {},
  data() {
    return {
      min: 1,
      max: 10,
      power: 5,
      speed: 5
    }
  },
  watch: {
    
  },
  methods: {
    toLowPower: function() { 
      if( this.power > this.min) {

        this.power = this.power - 1

        return this.power
      }
    },
    toUpPower: function() {
      if( this.power < this.max) {

        this.power = this.power + 1

        if(this.speed >= 1) {
          this.speed = this.speed - 1
        }
        
        return this.power 
      }  
    },

    toLowSpeed: function() { 
      if( this.speed > this.min) {

        this.speed = this.speed - 1

        return this.speed
      }
    },
    toUpSpeed: function() {
      if( this.speed < this.max) {

        this.speed = this.speed + 1

        if(this.power >= 1) {
          this.power = this.power - 1
        }
        
        return this.power 
      }  
    }

  }
}
</script>
