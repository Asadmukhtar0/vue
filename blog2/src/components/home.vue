<template>
   <div class="container">

       <table class="table table-bordered">
           <tr>
               <td>
                   #
               </td>
               <td>
                   <input type="text" class="form-control" v-model="name"  />
               </td>
               <td>
                   <input type="text" class="form-control" v-model="email" />
               </td>
               <td>
                   <input type="text" class="form-control" v-model="phone"  />
               </td>
               <td>
                   <button class="btn btn-danger" v-on:click="add()">Add</button>
               </td>
           </tr>
       </table>
       <div class="alert alert-danger" v-if="show">
           Please Add Data first
       </div>
       <table class="table table-bordered">
           <tr>
               <th>
                   ID
               </th>
               <th>
                   Name
               </th>
               <th>
                   Email
               </th>
               <th>
                   Phone
               </th>
               <th>
                   Delete
               </th>
           </tr>
           
           <tr v-for="(user, index) in users" :key="user.id">
                <th>
                   {{ user.id }}
               </th>
               <th>
                   {{ user.name }}
               </th>
               <th>
                   {{ user.email }}
               </th>
               <th>
                   {{ user.phone }}
               </th>
               <th>
                   <button class="btn btn-danger btn-sm" v-on:click="del(index)">Del</button>
               </th>
           </tr>
       </table>
   </div>
</template>
<script>

export default ({
    data(){
        return {
            name:null,
            email:null,
            phone:null,
            show:false,
            users : [
                {
                    id:1,
                    name:'asad',
                    email:'email@gmail.com',
                    phone:'03245434845'
                },
                {
                    id:2,
                    name:'asad',
                    email:'email@gmail.com',
                    phone:'03245434845'
                },
                {
                    id:3,
                    name:'asad',
                    email:'email@gmail.com',
                    phone:'03245434845'
                },
            ]
        }
    },
    methods:{
        del(id){
            this.users.splice(id);
        },
        add(){
            if(this.name != null && this.email != null && this.phone != null){
                var l = this.users.length;
                var n = l + 1;
                this.users.push({
                    id : n,
                    name: this.name,
                    email: this.email,
                    phone: this.phone
                });
                this.name= null
                this.email= null
                this.phone= null
            } else {
                this.show =true
            }
        }
    }
})
</script>
