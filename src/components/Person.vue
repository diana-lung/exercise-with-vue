<template>
<div>
    <label for="firstname">First Name</label>
    <input type="text" v-model="firstname" id="firstname"> <br>
    <label for="lastname">Last Name</label>
    <input type="text" v-model="lastname" id="lastname">
    <p>First name: {{ firstname }}, Last Name: {{ lastname }} </p>
    <p>This means my full name is: {{ getFullName }}</p>
    <p>My full name using the getter propriety will be the same: {{ fullName }}</p>
    <p>My initials are: {{ setInitials() }}</p>
    <p>My computed initials are: {{ initials }}</p>
    <button @click="changeInitials">Display Initials</button>
    <p>Current value: {{ count }}</p>
    <button @click="increment">Increment value</button>
    <button @click="decrement">Decrement value</button>
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
            return `${this.firstname} ${this.lastname}`;
        },
        fullName: {
            get() {
                return `${this.firstname} ${this.lastname}`;
            },
            set() {
                // do something
            },
        },
        setInitials2: {
            get() {
                return this.initials;
            },
            set(newInitials) {
                this.initials = newInitials;
            },
        }, 
    },
    methods: {
        setInitials() {
            let initialFirstName = this.firstname.split(' ').map((name) => name[0]).join(' ');
            let initialLastName = this.lastname.split(' ').map((name) => name[0]).join(' ');
            return `${initialFirstName} ${initialLastName}`; 
        },
        changeInitials() {
           this.setInitials2= 'Lung Diana';
        },
        increment() {
            this.count += 1;
        },
        decrement() {
            this.count -=1;
        },
    },
    watch: {
        initials(newValue, oldValue) {
            alert(`Old value: ${oldValue} New Value: ${newValue}`);
        },
        count(newValue) {
            if (newValue == 10) 
                alert('Congrats');
            if (newValue == -1)
                alert('Failure')
        }
    }
}
</script>