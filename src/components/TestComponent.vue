<template>
	<v-app>
		<v-main>
			<v-container fluid>
				<v-row justify="center">
					<v-col cols="4">
						<v-switch v-model="isId" inset label="idを適用" hide-details color="rgb(255, 0, 0)"></v-switch>
						<v-switch v-model="isIdImportant" inset label="idに!importantを追加" :disabled="!isId" hide-details color="rgb(128, 0, 0)"></v-switch>
						<v-switch v-model="isAppId" inset label="App.vue内idを適用" hide-details color="rgb(255, 247, 0)"></v-switch>
						<v-switch v-model="isAppIdImportant" inset label="App.vue内idに!importantを追加" :disabled="!isAppId" hide-details color="rgb(165, 160, 0)"></v-switch>
						<v-btn class="mt-4" small @click="reset"> reset </v-btn>
					</v-col>
					<v-col cols="2" style="text-align: center;" align-self="center">
						<h2 :id="idContents" :class="classContents" :style="styleContents">SCSS Text</h2>         
					</v-col>
					<v-col cols="4">
						<v-switch v-model="isStyle" inset label="Tag内にStyleを適用" hide-details color="rgb(255, 0, 255)"></v-switch>
						<v-switch v-model="isClass" inset label="classを適用" hide-details color="rgb(0, 255, 255)"></v-switch>
						<v-switch v-model="isClassImportant" inset label="class !importantを適用" hide-details color="rgb(0, 0, 255)"></v-switch>
						<v-switch v-model="isAppClass" inset label="App.vue内classを適用" hide-details color="rgb(0, 255, 0)"></v-switch>
						<v-switch v-model="isAppClassImportant" inset label="App.vue内class !importantを適用" hide-details color="rgb(0, 128, 0)"></v-switch>
					</v-col>
				</v-row>

				<!-- <h2>scss</h2>
				<h2 class="classstyle">scss + class scoped</h2>
				<h2 id="idstyle1">scss + id scoped</h2>
				<h2 class="classstyle" id="idstyle2">scss + id scoped + class scoped</h2>
				<h2 style="color: green;">scss + style api</h2>
				<h2 style="color: green;" id="idstyle3">scss + id scoped + style api</h2>
				<h2 style="color: green;" class="classstyle">scss + class scoped + style api</h2>
				<h2 style="color: green;" class="classstyle" id="idstyle4">scss + id scoped + class scoped + style api</h2>
				<br/>
				<h2 class="classstyleimportant">scss + class important scoped</h2>
				<h2 id="idstyleimportant1">scss + id important scoped</h2>
				<h2 id="idstyleimportant2" class="classstyleimportant">scss + id important scoped + class important scoped</h2>
				<h2 style="color: green;" id="idstyleimportant3">scss + id important scoped + style api</h2>
				<h2 style="color: green;" class="classstyleimportant">scss + class important scoped + style api</h2>
				<h2 style="color: green;" class="classstyleimportant" id="idstyleimportant4">scss + id scoped + class scoped + style api</h2>
				<h2 class="appvueclass">scss + id + class scoped + style api</h2> -->
			</v-container>
		</v-main>
	</v-app>
</template>
<script>
export default {
	name: 'TestComponent',
	components: {
	},
	data() {
	return {
			isId: false,
			isIdImportant: false,
			isAppId: false,
			isAppIdImportant: false,
			isClass: false,
			isClassImportant: false,
			isAppClass: false,
			isAppClassImportant: false,
			isStyle: false,
		}
	},
	computed:{
		idContents(){
			if(this.isId && this.isIdImportant){
				return "testidimportant"
			}else if(this.isId){
				return "testid"
			}else if(this.isAppId && this.isAppIdImportant){
				return "appvueidimportant"
			}else if(this.isAppId){
				return "appvueid"
			}else{
				return ""
			}
		},
		classContents(){
			if(this.isClass && this.isClassImportant && this.isAppClass && this.isAppClassImportant){
				return "testclass testclassimportant appvueclass appvueclassimportant"
			}
			else if(this.isClass && this.isClassImportant && this.isAppClass){
				return "testclass testclassimportant appvueclass"
			}else if(this.isClassImportant && this.isAppClass && this.isAppClassImportant){
				return "testclassimportant appvueclass appvueclassimportant"
			}else if(this.isClass && this.isAppClass && this.isAppClassImportant){
				return "testclass appvueclass appvueclassimportant"
			}else if(this.isClass && this.isClassImportant && this.isAppClassImportant){
				return "testclass testclassimportant appvueclassimportant"
			}
			else if(this.isClass && this.isClassImportant){
				return "testclass testclassimportant"
			}else if(this.isClass && this.isAppClass){
				return "testclass appvueclass"
			}else if(this.isClass && this.isAppClassImportant){
				return "testclass appvueclassimportant"
			}else if(this.isClassImportant && this.isAppClass){
				return "testclassimportant appvueclass"
			}else if(this.isClassImportant && this.isAppClassImportant){
				return "testclassimportant appvueclassimportant"
			}else if(this.isAppClass && this.isAppClassImportant){
				return "appvueclass appvueclassimportant"
			}
			else if(this.isClassImportant){
				return "testclassimportant"
			}else if(this.isClass){
				return "testclass"
			}else if(this.isAppClass){
				return "appvueclass"
			}else if(this.isAppClassImportant){
				return "appvueclassimportant"
			}else{
				return ""
			}
		},
		styleContents(){
			if(this.isStyle){
				return "color: rgb(255, 0, 255);"
			}else{
				return ""
			}
		},
	},
	watch:{
		isId(){
			if(!this.isId){
				this.isIdImportant = false
			}else if(this.isId){
				this.isAppId = false
				this.isAppIdImportant = false
			}
		},
		isAppId(){
			if(!this.isId){
				this.isAppIdImportant = false
			}else if(this.isAppId){
				this.isId = false
				this.isIdImportant = false
			}
		}
	},
	methods: {
		reset(){
			this.isId = false
			this.isIdImportant = false
			this.isAppId = false
			this.isAppIdImportant = false
			this.isClass = false
			this.isClassImportant = false
			this.isAppClass = false
			this.isAppClassImportant = false
			this.isStyle = false
		}
	}
}
</script>
<style scoped>
#testid{
	color: red;
}
#testidimportant{
	color: rgb(128, 0, 0) !important;
}
.testclass{
	color: rgb(0, 255, 255);
}
.testclassimportant{
	color: rgb(0, 0, 255) !important;
}
#idstyle1{
	color: red;
}
#idstyle2{
	color: red;
}
#idstyle3{
	color: red;
}
#idstyle4{
	color: red;
}
#idstyleimportant1{
	color: fuchsia !important;
}
#idstyleimportant2{
	color: fuchsia !important;
}
#idstyleimportant3{
	color: fuchsia !important;
}
#idstyleimportant4{
	color: fuchsia !important;
}
.classstyle{
	color: blue;
}
.classstyleimportant{
	color: aqua !important;
}
</style>