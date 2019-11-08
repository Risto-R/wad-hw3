<template>
    <div>
        <div class="content">
            <div id="profile-container" class="tab" v-bind:class="{ active: active }">
                <Profile :user="user"></Profile>
            </div>
            <div id="courses-container" class="tab" v-bind:class="{ active: !active }">
                <Courses :courses="courses"></Courses>
            </div>
        </div>
        <div class="controls">
            <button id="profile-button" class="pill" v-bind:class="{'is-active': active === true,active: active}"
                    name="button" @click="active=true">Profile
            </button>
            <button id="courses-button" class="pill" :class="{'is-active': active === false,active: !active}"
                    name="button" @click="active=false">Courses
            </button>
        </div>
    </div>
</template>

<script>
    import Profile from '../components/Profile';
    import Courses from "../components/Courses";
    import User from "../models/User";
    import Course from "../models/Course";

    export default {
        name: "MainContent",
        components: {Profile, Courses},
        data: () => {
            return {
                active: true,
                user: new User("John", "Doe", "11/10/1990", "Faculty of Science and Technology", 2.5),
                courses: [new Course("Web Application Development", 3, 100),
                    new Course("Introduction to Data Science", 3, 91),
                    new Course("Software Engineering", 3, 87),
                    new Course("Algorithms and data structures", 3, 85)]
            }
        }
    }
</script>

<style scoped>

</style>