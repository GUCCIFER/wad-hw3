<template>
    <section id="container">
        <section id="main">
            <div class="content">
                <Profile :userProp="user" :coursesProp="courses" v-bind:class="{'tab active':isOn, 'tab':isOff}"/>
                <Courses :coursesProp="courses" v-bind:class="{'tab active':isOff, 'tab':isOn}"/>
            </div>
            <div class="controls">
                <button id="profile-button" @click="change" v-bind:class="{'pill active':isOn, 'pill': isOff}">Profile
                </button>
                <button id="courses-button" @click="change" v-bind:class="{'pill active':isOff, 'pill': isOn}">Courses
                </button>
            </div>
        </section>
    </section>
</template>

<script>
    import Courses from "./Courses";
    import Profile from "./Profile";
    import User from "./User";
    import Course from "./Course";

    export default {
        name: "Main",
        components: {Courses, Profile},
        data: () => {
            return {
                isOn: true,
                isOff: false,
                user: new User("Martin", "Vahe", "11.11.2001", "IT", "1.88"),
                courses: [
                    new Course("Business Analysis", 1, 70),
                    new Course("Computer Graphics", 1, 84),
                    new Course("Artificial Intelligence", 2, 56),
                    new Course("Neural Networks", 2, 71)
                ]
            }
        },
        methods: {
            change: function () {
                if (this.isOn) {
                    this.isOn = false;
                    this.isOff = true;
                } else {
                    this.isOn = true;
                    this.isOff = false;
                }
            }
        }
    }
</script>

<style scoped>

</style>