<template>
	<div class="container">
		<form @submit="createteacher" method="post">
			<div class="col-lg-12">
                <label for="">Teacher Name</label>
                <input type="text" class="form-control" name="name" v-model="teacher.name" id="" />
            </div>
            <div class="col-lg-12">
                <label for="">Phone</label>
                <input type="text" class="form-control" name="phone" v-model="teacher.phone" id="" />
            </div>
            <div class="col-lg-12">
                <label for="">Email</label>
                <input type="text" class="form-control" name="email" v-model="teacher.email" id="" />
            </div>
            <div class="col-lg-12">
                <button type="submit" class="btn btn-info float-right">Save</button>
            </div>
		</form>
		<table class="table table-bordered">
				<tr v-for="teacher in teachers" :key="teacher.id">
						<th>
							{{ teacher.id }}
						</th>
						<th>
							{{ teacher.name }}
						</th>
						<th>
							{{ teacher.email }}
						</th>
						<th>
							{{ teacher.phone }}
						</th>
				</tr>
		</table>
	</div>
</template>
<script type="text/javascript">	
	import axios from 'axios'
	export default ({
		data(){
			return {
				teachers:null,
				teacher:{
					name:null,
					phone:null,
					email:null,
				}
			}
		},
		methods : {
			createteacher(e){
				e.preventDefault();
				axios.post('http://localhost:8000/api/add/teachers',this.teacher).then(response =>{
					console.log(response); 
				}),
				alert("added");
			}
		},
		mounted(){
			axios.get('http://localhost:8000/api/teachers').then(response =>{
				this.teachers = response.data.response 
			})
		}

	}); 
</script>