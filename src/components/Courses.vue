<template>
    <div id="courses-container">
        <h1 class="title">Courses</h1>
        <table id="courses">
            <thead>
            <tr>
                <th>#</th>
                <th>Course Title</th>
                <th>Semester</th>
                <th>Grade</th>
            </tr>
            </thead>
            <tbody>
                <tr v-for="(course, index) in coursesProp" :key="index">
                    <td>{{index+1}}</td>
                    <td>{{course.title}}</td>
                    <td>{{course.semester}}</td>
                    <td>{{course.grade}}</td>
                </tr>
            </tbody>
        </table>
        <br>
        <br>
        <div>
            <button id="add-course-button" @click="showInput" class="blue-button">+</button>
            <span v-bind:id=add_course>
                <input class="input" type="text" v-model="title" placeholder="Course title" id="title">
                <input class="input" type="number" v-model="semester" min="1" max="8" placeholder="Semester" id="semester" ref="semester">
                <input class="input" type="number" v-model="grade" min="0" max="100" placeholder="Grade" id="grade" ref="grade">
                <button class="green-button" id="save-course" @click="addCourse">Save</button>
                <button class="grey-button" id="cancel-course" @click="resetInput">Cancel</button>
            </span>
        </div>
    </div>
</template>

<script>
    import Course from "./Course";

    export default {
        name: "Courses",
        data: () => {
            return {
                title: "",
                semester: "",
                grade: "",
                add_course:'add-course'
            }
        },

        props:{
            coursesProp: Array
        },

        methods: {
            showInput: function () {
                if (this.add_course === 'add-course')
                    this.add_course = 'add-course-active';
                else
                    this.add_course = 'add-course';
            },

            addCourse: function(){
                let course = new Course(this.title, this.semester, this.grade);
                this.coursesProp.push(course);
                this.title = "";
                this.semester = "";
                this.grade = "";
                this.add_course = 'add-course'
            },

            resetInput: function(){
                this.title = "";
                this.semester = "";
                this.grade = "";
                if (this.add_course === 'add-course')
                    this.add_course = 'add-course-active';
                else
                    this.add_course = 'add-course';
                
            }
        }
    }
</script>

<style scoped>

</style>