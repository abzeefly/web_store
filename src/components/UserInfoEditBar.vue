<template>
    <b-sidebar id="sidebar-edit" title="User Information" shadow>
      <div>
        <b-card bg-variant="light">
            <b-form-group label="Full Name:">
                <b-form-input :disabled="validate == 1" v-model="user.info.fullname"></b-form-input>
            </b-form-group>
            <b-form-group label="Email:">
                <b-form-input :disabled="validate == 1" v-model="user.info.email"></b-form-input>
            </b-form-group>
            <b-form-group label="Username:">
                <b-form-input :disabled="validate == 1" v-model="user.info.username"></b-form-input>
            </b-form-group>
            <b-form-group label="Password:">
                <b-form-input :disabled="validate == 1" v-model="user.info.password"></b-form-input>
            </b-form-group>
            <b-form-group label="Address:">
                <b-form-input :disabled="validate == 1" v-model="user.info.address"></b-form-input>
            </b-form-group>
        </b-card>
        </div>
        <template #footer="{ }">
                <div class="d-flex bg-dark text-light align-items-center px-3 py-2">
                    <b-button size="sm" @click="edit" class="mr-auto"><strong >Edit</strong></b-button>
                    <b-button size="sm" @click="save" ><strong>Save</strong></b-button>
                </div>
        </template>
    </b-sidebar>
</template>

<script>
export default {
    name: 'UserInfoEditBar',
        props: {
            user: Object,
        },
    data(){
        return{
            validate: 1
        }
    },
    methods:{
        edit(){
            this.validate = 0
            return
        },
        save(){
            this.validate = 1
            return
        }
    }
}
</script>