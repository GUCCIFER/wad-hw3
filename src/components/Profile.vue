<template>
    <div id="profile-container">
        <div id="profile">
            <div class="avatar">
                <img src="../assets/me.png" id="picture" alt="My picture">
            </div>
            <div class="info">
                <ul>
                    <li id="name">{{userProp.first}} {{userProp.last}}</li>
                    <li id="birthdate">{{userProp.birth}}</li>
                    <li id="faculty">{{userProp.fac}}</li>
                </ul>
            </div>
            <div id="gpa">
                <strong>{{calculateGPA()}}</strong>
            </div>
            <div class="clear-fix"></div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Profile",

        props:{
            userProp: Object,
            coursesProp: Array
        },

        methods: {
            calculateGPA: function(){
                let sum = 0;
                for(var i = 0; i<this.coursesProp.length; i++){
                    var grade = this.coursesProp[i].grade;
                    if (grade >= 90) {
                        sum += 4;
                    } else if (grade >= 80) {
                        sum += 3;
                    } else if (grade >= 70) {
                        sum += 2;
                    } else if (grade >= 60) {
                        sum += 1;
                    } else if (grade >= 50) {
                        sum += 0.5;
                    } else {
                        sum += 0;
                    }
                }
                let num = sum/this.coursesProp.length;
                return Math.round(num * 100) / 100;
            },
        }
    }



</script>

<style scoped>

</style>