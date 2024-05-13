<template>
  <div>
    <h1>Students List</h1>
    <ul>
      <li v-for="(student, index) in students" :key="index">
        <span>{{ student.name }}</span>
        <span v-if="student.age >= 18"> (Adult)</span>
        <span v-else> (Minor)</span>
        <input type="checkbox" v-model="student.attendance">
        <span v-if="student.attendance">Present</span>
        <span v-else>Absent</span>
      </li>
    </ul>
    <h2>Add New Student</h2>
    <div>
      <label for="name">Name:</label>
      <input type="text" id="name" v-model="newStudentName">
      <label for="age">Age:</label>
      <input type="number" id="age" v-model.number="newStudentAge">
      <button @click="addStudent">Add Student</button>
    </div>
    <p>Total Students: {{ totalStudents }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      students: [
        { name: 'John', age: 20, attendance: true },
        { name: 'Jane', age: 17, attendance: false }
      ],
      newStudentName: '',
      newStudentAge: ''
    };
  },
  methods: {
    addStudent() {
      if (this.newStudentName.trim() !== '' && this.newStudentAge !== '') {
        this.students.push({
          name: this.newStudentName,
          age: parseInt(this.newStudentAge),
          attendance: false
        });
        this.newStudentName = '';
        this.newStudentAge = '';
      }
    }
  },
  computed: {
    totalStudents() {
      return this.students.length;
    }
  }
};
</script>

<style>

</style>
