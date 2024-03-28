<script>
export default {
    data() {
        return {
            numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100],
            generatedNumber: Math.floor(Math.random() * 100) + 1,
            numberPicked: null,
            HigherOrLower: "",
            numberSelectedList: [],
            Result: "",
            showSubmitButton: true,
            showStartAgainButton: false,
            showAttemptsRemaining: true,
            attemptsRemaining: 10
        }
    },
    methods: {
        submitButton() {
            if (this.generatedNumber == this.numberPicked) {
                this.Result = "Correct number has been matched " + "which is " + this.generatedNumber,
                this.HigherOrLower = "",
                this.showSubmitButton = false,
                this.numberSelectedList.push(this.numberPicked),
                this.showStartAgainButton = true,
                this.showAttemptsRemaining = false
            
            } else {
                if (this.generatedNumber > this.numberPicked) {
                    this.HigherOrLower = "Number selected is too low"
                } else {
                    this.HigherOrLower = "Number selected is too high"
                }
                this.numberSelectedList.push(this.numberPicked),
                this.attemptsRemaining --
                if (this.attemptsRemaining == 0) {
                    this.Result = "Game over, you was unable to match the number " + "which is " + this.generatedNumber,
                    this.HigherOrLower = "",
                    this.showSubmitButton = false,
                    this.showStartAgainButton = true
                }
            }
        },
        StartAgain() {
            window.location.reload();
        }
    }
}
</script>



<template>
    <form @submit.prevent="submitButton">
        <label class="px-2 font-bold text-2xl">Pick a number:</label>
        <select v-model="numberPicked">
            <option v-for="number in numbers" v-show="showSubmitButton">{{ number }}</option>
        </select>
        <button class="border-2 border-black p-1 mx-3 font-bold" v-show="showSubmitButton">Submit Number</button>
        
        <div class="space-y-4 border-2 border-black mt-6 p-4">
            <p class="font-bold text-2xl">{{ Result }}</p>
            <p class="font-bold text-2xl">{{ HigherOrLower }}</p>
            <p class="font-bold text-2xl">{{ numberSelectedList }}</p>
            <p class="font-bold text-2xl" v-show="showAttemptsRemaining">You have {{ attemptsRemaining }} remaining</p>
            <button v-show="showStartAgainButton" v-on:click="StartAgain" class="border-2 border-black p-1 font-bold text-2xl">Start Again</button>
        </div>
    </form>
</template>