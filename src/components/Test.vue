<template>
    <div id="visa">
        <h1>Create a new Vue Account</h1>
        <form>
            <label for="full name">Full name</label>
            <input type="text" v-model="name" required>
            <br>
            <label v-if="msg.name">{{msg.name}}</label>

            <label for="email">Email Address</label>
            <input type="text" v-model="email" required>
            <br>
            <span v-if="msg.email">{{msg.email}}</span>

            <label for="password">Password</label>
            <input type="text" v-model="password" required>
            <br>
            <span v-if="msg.password">{{msg.password}}</span>

            <label for="phone">Phone</label>
            <input type="text" v-model="phone" required>
            <br>
            <span v-if="msg.phone">{{msg.phone}}</span>
            
            <br>
            <span v-if="msg.isEmpty">{{msg.isEmpty}}</span>
        </form>
    </div>
</template>
<script>
export default {
    name: "Test",
    data() {
        return {
            name: "",
            password: "",
            email: "",
            phone: "",
            isEmpty: "",
            msg: [],
        }
    },
    watch: {
        name(value) {
            this.name = value;
            this.validateName(value);
        },
        email(value) {
            this.email = value;
            this.validateEmail(value);
        },
        password(value) {
            this.password = value
            this.validatePassword(value)
        },
        phone(value) {
            this.phone = value
            this.validatePhone(value)
        },
        isEmpty(value) {
            this.isEmpty = value
            this.validateisEmpty(value)
        }
    },
    methods: {
        validateName(value) {
            if(value.length >= 3 && value.length <= 12) {
                this.msg["name"] = "Your name is valid";
            } else {
                this.msg["name"] = "Name must be between 3-12 letters"
            }
        },
        validateEmail(value) {
            if (/^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/.test(value)) {
                this.msg["email"] = "Your mail is valid";
            } else {
                this.msg["email"] = "Invalid Email Adress"
            }
        },
        validatePassword(value) {
            let difference = 8 - value.length
            if(value.length<8) {
                this.msg["password"] = 
                "Must be 8 characters! " 
                +difference+ 
                " characters left"
            } else {
                this.msg["password"] = ""
            }
        },
        validatePhone(value) {
            if(value > 0) {
                this.msg["phone"] = "Your phone is valid"
            } else {
                this.msg["phone"] = "Please use number characters"
            }
        }
    }
}
</script>

<style scoped>
    #visa {
        display: flex;
        flex-direction: column;
        width: 600px;
        margin: 0 auto;
    }
    form {
        display: flex;
        flex-direction: column;
    }
</style>