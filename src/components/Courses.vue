<template>
    <div>
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
            <tr v-for="(course,index) in Courses" v-bind:key="index">
                <td>{{index}}</td>
                <td>{{course.title}}</td>
                <td>{{course.semester}}</td>
                <td>{{course.grade}}</td>
            </tr>
            </tbody>
        </table>
        <br>
        <br>
        <div>
            <button id="add-course-button" class="blue-button" @click="formActive = !formActive">+</button>
            <span id="add-course" v-bind:class="{active:formActive}">
                <form v-on:submit.prevent="addNewCourse">
                    <input v-model="newTitle" type="text" placeholder="Course title" id="title">
                    <input v-model="newSemester" type="number" min="1" max="8" placeholder="Semester" id="semester">
                    <input v-model="newGrade" type="number" min="0" max="100" placeholder="Grade" id="grade">
                    <button class="green-button" id="save-course" @click="formActive = !formActive;addNewCourse ">Save</button>
                    <button class="grey-button" id="cancel-course" @click="formActive = !formActive">Cancel</button>
                </form>
            </span>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Courses",
        props: {Courses: Array},
        data: () => {
            return {
                formActive: false,
                newTitle:"",
                newSemester:"",
                newGrade:""
            }
        },
        methods:{
            addNewCourse:function(){
                this.Courses.push({
                    title: this.newTitle,
                    semester: this.newSemester,
                    grade: this.newGrade
                })
            }
        }
    }
</script>

<style scoped>

</style>