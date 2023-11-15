<script>
import { evaluate } from "mathjs";
export default {
  data() {
    return {
      bg: 1,
      expression: "",
    };
  },
  methods: {
    theme1() {
      this.bg = 1;
    },
    theme2() {
      this.bg = 2;
    },
    theme3() {
      this.bg = 3;
    },
    calculate() {
      this.expression = this.expression.replace(/\s/g, "");
      this.expression = evaluate(this.expression);
      if (this.expression == Infinity) {
        this.expression = "Infinity";
      } else if (
        typeof this.expression === "number" &&
        !Number.isInteger(this.expression)
      ) {
        this.expression = this.expression.toFixed(4);
      }
    },
    reset() {
      this.expression = "";
    },
  },
};
</script>

<template>
  <main
    class="app h-screen sm:flex sm:p-0 p-4 justify-center items-center flex-col"
    :class="{
      'bg-theme1-mainBg': bg === 1,
      'bg-theme2-mainBg': bg === 2,
      'bg-theme3-mainBg': bg === 3,
    }"
  >
    <div class="flex max-w-lg w-full mb-4">
      <!-- Left side -->
      <div class="flex items-center justify-start w-1/2">
        <h1
          class="text-4xl"
          :class="{
            'text-theme1-text2': bg === 1,
            'text-theme2-text2': bg === 2,
            'text-theme3-text2': bg === 3,
          }"
        >
          calc
        </h1>
      </div>

      <!-- Right side -->
      <div class="flex items-center justify-end w-1/2">
        <span
          class="text-xs mr-5"
          :class="{
            'text-theme1-text2': bg === 1,
            'text-theme2-text2': bg === 2,
            'text-theme3-text2': bg === 3,
          }"
          >THEME</span
        >
        <div class="flex flex-col">
          <div class="space-x-4 justify-center text-center">
            <span
              :class="{
                'text-theme1-text2': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
              >1</span
            >
            <span
              :class="{
                'text-theme1-text2': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
              >2</span
            >
            <span
              :class="{
                'text-theme1-text2': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
              >3</span
            >
          </div>
          <div
            class="flex items-center space-x-2 p-1 rounded-full"
            :class="{
              ' bg-theme1-toggleBg': bg === 1,
              'bg-theme2-toggleBg': bg === 2,
              'bg-theme3-toggleBg': bg === 3,
            }"
          >
            <!-- Port 1 -->
            <button
              class="group relative flex items-center justify-center w-4 h-4 border border-transparent rounded-full transition-all"
              :class="{
                'bg-theme1-keyBg2': bg === 1,
              }"
              @click="theme1"
            ></button>

            <!-- Port 2 -->
            <button
              class="group relative flex items-center justify-center w-4 h-4 border border-transparent rounded-full transition-all"
              :class="{ 'bg-theme2-keyBg2': bg === 2 }"
              @click="theme2"
            ></button>

            <!-- Port 3 -->
            <button
              class="group relative flex items-center justify-center w-4 h-4 border border-transparent rounded-full transition-all"
              :class="{ 'bg-theme3-keyBg2': bg === 3 }"
              @click="theme3"
            ></button>
          </div>
        </div>
      </div>
    </div>
    <div
      class="sm:flex max-w-lg w-full p-4 rounded-lg mb-4"
      :class="{
        ' bg-theme1-screenBg': bg === 1,
        'bg-theme2-screenBg': bg === 2,
        'bg-theme3-screenBg': bg === 3,
      }"
    >
      <div class="flex-1"></div>
      <h1
        class="text-7xl"
        :class="{
          'text-theme1-text2': bg === 1,
          'text-theme2-text2': bg === 2,
          'text-theme3-text2': bg === 3,
        }"
        v-if="expression != ''"
      >
        {{ expression }}
      </h1>
      <h1
        class="text-7xl"
        :class="{
          'text-theme1-text2': bg === 1,
          'text-theme2-text2': bg === 2,
          'text-theme3-text2': bg === 3,
        }"
        v-else
      >
        0
      </h1>
    </div>
    <div
      class="max-w-lg w-full p-4 rounded-lg"
      :class="{
        'bg-theme1-toggleBg ': bg === 1,
        'bg-theme2-toggleBg': bg === 2,
        'bg-theme3-toggleBg': bg === 3,
      }"
    >
      <div class="flex w-full mb-4">
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '7'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              7
            </p>
          </button>
        </div>
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '8'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              8
            </p>
          </button>
        </div>
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '9'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              9
            </p>
          </button>
        </div>
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-3 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg1 shadow-theme1-keySd1': bg === 1,
              'bg-theme2-keyBg1 shadow-theme2-keySd1': bg === 2,
              'bg-theme3-keyBg1 shadow-theme3-keySd1': bg === 3,
            }"
            @click.stop="expression -= expression"
          >
            <p
              class="text-2xl text-theme1-keyBg3"
              :class="{
                'text-theme1-text2': bg === 1,
                'text-theme1-text2': bg === 2,
                'text-theme1-text2': bg === 3,
              }"
            >
              DEL
            </p>
          </button>
        </div>
      </div>
      <div class="flex w-full mb-4">
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '4'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              4
            </p>
          </button>
        </div>
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '5'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              5
            </p>
          </button>
        </div>
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '6'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              6
            </p>
          </button>
        </div>
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '+'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              +
            </p>
          </button>
        </div>
      </div>
      <div class="flex w-full mb-4">
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '1'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              1
            </p>
          </button>
        </div>
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '2'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              2
            </p>
          </button>
        </div>
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '3'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              3
            </p>
          </button>
        </div>
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '-'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              -
            </p>
          </button>
        </div>
      </div>
      <div class="flex w-full mb-4">
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '.'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              .
            </p>
          </button>
        </div>
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '0'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              0
            </p>
          </button>
        </div>
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '/'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              /
            </p>
          </button>
        </div>
        <div class="w-1/4 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-3/5 w-4/5 rounded-lg"
            :class="{
              'bg-theme1-keyBg3 shadow-theme1-keySd3': bg === 1,
              'bg-theme2-keyBg3 shadow-theme2-keySd3': bg === 2,
              'bg-theme3-keyBg3 shadow-theme3-keySd3': bg === 3,
            }"
            @click.stop="expression += '*'"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text1': bg === 1,
                'text-theme2-text2': bg === 2,
                'text-theme3-text2': bg === 3,
              }"
            >
              x
            </p>
          </button>
        </div>
      </div>
      <div class="flex w-full mb-4">
        <div class="w-1/2 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-4/5 w-5/6 rounded-lg"
            :class="{
              'bg-theme1-keyBg1 shadow-theme1-keySd1': bg === 1,
              'bg-theme2-keyBg1 shadow-theme2-keySd1': bg === 2,
              'bg-theme3-keyBg1 shadow-theme3-keySd1': bg === 3,
            }"
            @click="reset"
          >
            <p
              class="text-2xl"
              :class="{
                'text-theme1-text2': bg === 1,
                'text-theme2-text1': bg === 2,
                'text-theme3-text1': bg === 3,
              }"
            >
              RESET
            </p>
          </button>
        </div>
        <div class="w-1/2 flex items-center justify-center">
          <button
            class="shadow-sm p-2 sm:w-4/5 w-5/6 rounded-lg"
            :class="{
              'bg-theme1-keyBg2 shadow-theme1-keySd2': bg === 1,
              'bg-theme2-keyBg2 shadow-theme2-keySd2': bg === 2,
              'bg-theme3-keyBg2 shadow-theme3-keySd2': bg === 3,
            }"
            @click="calculate"
          >
            <p
              class="text-3xl"
              :class="{
                'text-theme1-text2': bg === 1,
                'text-theme2-text1': bg === 2,
                'text-theme3-text3': bg === 3,
              }"
            >
              =
            </p>
          </button>
        </div>
      </div>
    </div>
  </main>
</template>
