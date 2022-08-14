<template>
  <div>
<div class="open-text">ברוכים הבאים! כאן תוכלו להכניס את השאלות שיופיעו בחדר הבריחה.</div>
        <div class="open-text">לפני שנתחיל, תבחרו את הבה"ד שלכם, את הקורס ואת הלומדה שאתם רוצים לכתוב להם שאלות</div>
        <select class="bahad dropdown" name="bahad" v-model="bahad">
            <option value="" disabled selected>מאיזה בה"ד אתם?</option>
            <option v-for="bahad, key in COURSES" :key="'bahad' + key">{{addSpace(`${this.key}`)}}</option>
        </select>
        <select class="course dropdown" name="course" v-model="course" :disabled="this.bahad? true: ''">
            <option value="" disabled selected>איזה קורס אתם מעבירים?</option>
            <option v-for="course in COURSES" :key="course">{{addSpace(course)}}</option>
        </select>
        <select class="area dropdown" name="area" v-model="area" disabled>
            <option value="" disabled selected>לאיזה אזור לומדות תרצו להכניס שאלות?</option>
        </select>
        <button id="to-input" class="btn" disabled>סיימתי!</button>
  </div>
</template>

<script>
export default {
    name: "open-screen",
    data() {
        return {
          "bahad": "",
          "course": "",
          "area": "",
          "COURSES":{
            'בה"ד-6': ["קורס-בהד-6", "קורס-2", "קורס-3", "קורס-4"],
            'בה"ד-7': ["קורס-בהד-7", "קורס-2", "קורס-3", "קורס-4"],
            'בה"ד-10': ["קורס-בהד-10", "קורס-2", "קורס-3", "קורס-4"],
            'בה"ד-11': ["קורס-1", "קורס-2", "קורס-3", "קורס-4"],
            'בה"ד-13': ["קורס-1", "קורס-2", "קורס-3", "קורס-4"],
            'בה"ד-20': ["קורס-1", "קורס-2", "קורס-3", "קורס-4"],
            'בה"ד-חינוך': ["קורס-1", "קורס-2", "קורס-3", "קורס-4"],
            "מפקדה": ["קורס-1", "קורס-2", "קורס-3", "קורס-4"],
          }
        }
    },
    methods: {
      addSpace(phrase) {
        return(phrase.replace(/-/g, " "));
      },
      removeSpace(phrase) {
        return(phrase.replace(" ", /-/g));
      }
    }
}
</script>

<style scoped>
.dropdown {
    margin: 3vh 1vw 5vh 1vw;
    font-size: 4vmin;
    border-radius: 0.2em;
}

.dropdown:disabled,
button:disabled {
    background-color: rgb(251, 195, 203);
}

.btn {
    font-size: 3vmin;
    display: block;
    margin: 2vh auto;
    border-radius: 0.2em;
    border: solid 1px;
    padding: 1vh 5vw;
    background-color: rgb(196, 104, 196);
    user-select: none;
}
</style>