<template>
<div id="visa">
    <h1>Tracer Study</h1>
    <form>
        <!-- <label for="first name">First Name:</label>
        <input type="text" required> -->
        <!-- label di field isian namanya placeholder -->
        <!-- <br>
        <label for="last name">Last Name:</label>
        <input type="text" required>
        <br>
        <label for="country">Nationality:</label>
        <input type="text" required>
        <br>
        <label for="passport number">Passport Number:</label>
        <input type="text" required>

        <label for="duration">Duration of stay:</label>
        <input type="text" required>
        <br><br> -->
        <br>
        <!-- <div class="previous" v-for="(applicant, counter) in applicants" v-bind:key="counter">
            <span @click="deleteVisa(counter)">x</span>
            <label for="duration">{{counter+1}}. Previous Visa:</label>
            <input type="text" v-model="applicant.previous" required>
            <label for="duration">Year of expiration:</label>
            <input type="text" v-model="applicant.expiration" required>

            <div v-for="(answer, count) in applicant.answers" v-bind:key="count">
                <label for="duration">Option {{count+1}}</label>
                <input type="text" v-model="answer.option" required>
                <span @click="deleteMulti(applicant, count)">x</span>
            </div>
            <button @click="addMulti(applicant)">Tambah pilihan jawaban</button>
        </div> -->
        <div v-for="(questionnaire, counter) in questionnaires" v-bind:key="counter">
            <div class="previous" v-for="(currQuestion, qCount) in questionnaire.questions" v-bind:key="qCount">
                <span @click="deleteQuestion(questionnaire, qCount)">x</span>
                <label for="duration">Pertanyaan {{qCount+1}}</label>
                <input type="text" v-model="currQuestion.question" required>

                <div v-for="(answer, count) in currQuestion.answers" v-bind:key="count">
                    <label for="duration">Option {{count+1}}</label>
                    <input type="text" v-model="answer.option" required>
                    <span @click="deleteOption(currQuestion, count)">x</span>
                </div>
                <button @click="addOption(currQuestion)">Tambah pilihan jawaban</button>
            </div>
            <button @click="addQuestion(questionnaire)">Tambah pertanyaan</button>
        </div>
        <br>
    </form>
</div>
</template>

<script>
export default ({
    name: 'FormDisplay',
    props: {
        msg: String
    },
    data() {
        return {
            // applicants: [{
            //     previous: '',
            //     expiration: '',
            //     answers: [{
            //         option: ''
            //     }]
            // }]
            questionnaires: [{
                name: '',
                schedule: '',
                questions: [{
                    question: '',
                    answers: [{
                        option: ''
                    }]
                }]
            }]
        }
    },
    methods: {
        addQuestion(questionnaire) {
            questionnaire.questions.push({
                question: '',
                answers: [{
                    option: ''
                }]
            })
        },
        deleteQuestion(questionnaire, counter) {
            questionnaire.questions.splice(counter, 1);
        },
        addOption(currQuestion) {
            currQuestion.answers.push({
                option: ''
            });
        },
        deleteOption(currQuestion, count) {
            currQuestion.answers.splice(count, 1);
        }
    }
})
</script>

<style scoped>
#visa {
    margin: 20px auto;
    max-width: 700px;
}

label {
    display: block;
    margin: 20px 0 10px;
}

input {
    font-size: 30px;
    border: 1px double rgb(102, 97, 96);
    border-radius: 4px;
}

button {
    font-size: 16px;
    background: rgb(78, 78, 191);
    padding: 0.4rem 1.3rem;
    text-align: center;
    border: none;
    cursor: pointer;
    border-radius: 4px;
    margin: 10px;
    color: aliceblue;
}

span {
    width: 30px;
    float: right;
    cursor: pointer;
}

span:hover {
    color: brown;
}

.previous {
    border: 1.5px solid;
    padding: 5px;
    margin-bottom: 10px;
}
</style>
