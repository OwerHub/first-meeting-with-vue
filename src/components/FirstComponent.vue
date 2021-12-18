<template>
	<div>
		<div class="udvozletDiv">I am {{propsName}}</div>
	</div>
</template>


<script>
export default{
	name: "FirstComponent",
	props:{
		propsName: String
	}
}
</script>
