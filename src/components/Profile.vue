<template>

    <div id="profile">
        <div class="avatar">
            <img src="../assets/me.png" id="picture" alt="My picture">
        </div>
        <div class="info">
            <ul>
                <li id="name">{{user.firstname}} {{user.lastname}}</li>
                <li id="birthdate">{{user.birthdate}}</li>
                <li id="faculty">{{user.faculty}}</li>
            </ul>
        </div>
        <div>
            <strong>{{user.gpa}}</strong>
        </div>
        <div class="clear-fix"></div>
    </div>

</template>

<script>
    export default {
        name: "Profile",
        props: {
            user: Object
        },
        methods:{
            gpaUpdate:function(){
                var totalgpa = 0;
                for(var grade in this.Courses.grade){
                    if(grade > 90){
                        totalgpa += 4;
                    }
                    if(grade > 80 && grade <=90){
                        totalgpa += 3;
                    }
                    if(grade > 70 && grade <=80){
                        totalgpa += 2;
                    }
                    if(grade > 60 && grade <=70){
                        totalgpa += 1;
                    }
                    if(grade > 50 && grade <= 60){
                        totalgpa += 0.5;
                    }
                }
                return totalgpa/this.Courses.length;
            }
        }
    }
</script>

<style scoped>

</style>