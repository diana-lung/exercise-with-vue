<template>
<div>
    <label for="firstname">First Name</label>
    <input type="text" v-model="firstname" id="firstname"> <br>
    <label for="lastname">Last Name</label>
    <input type="text" v-model="lastname" id="lastname">
    <p>First name: {{ firstname }}, Last Name: {{ lastname }} </p>
    <p>This means my full name is: {{ getFullName }}</p>
    <p>My full name using the getter propriety will be the same: {{ fullName }}</p>

    <p>My computed initials are: {{ initials }}</p>
    <button @click="setInitials">Set Initials</button>
    <div v-if="false">
        <p>Current value: {{ count }}</p>
        <button @click="increment">Increment value</button>
        <button @click="decrement">Decrement value</button>
    </div>
</div>
</template>

<script>
export default {
    name: 'Person',
    data() {
        return {
            firstname: '',
            lastname: '',
            initials: '',
            count: 0,
        }
    },
    computed: {
        getFullName() {
            return this.firstname + ' ' + this.lastname;
        },
        fullName: {
            get() {
                return this.firstname + ' ' + this.lastname;
            },
            set() {
                // do something
            },
        },
    },
    methods: {
        increment() {
            this.count += 1;
        },
        decrement() {
            this.count -=1;
        },
        setInitials() {
            let initialFirstName = this.firstname.split(' ').map((name) => name[0]).join(' ');
            let initialLastName = this.lastname.split(' ').map((name) => name[0]).join(' ');
            this.initials = `${initialFirstName} ${initialLastName}`;
        },
    },
}
</script>