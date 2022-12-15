<template>
    <main>
      <h1>Zoznam ľudí</h1>
      <section class="list">
        <section v-for="person of persons" v-bind:key="person"
        v-bind:class="{'card-container':true,'card':true,'adult':age(person)>=18,'above50':age(person)>=50}">
		<!--v tomto prípade clase priradíme objekt, ktorého vlastnosti predstavujú jednotlivé triedy a ich hodnoty predstavujú bool vyjadrujúci, kedy sa má daná trieda pridať danému elemntu-->
		<!--alebo takto tu to poriešime ternárnym operátorom...
		<section v-for="person of persons" v-bind:key="person" 
		v-bind:class="person.age>=18 ? 'adult card-container card' : 'card-container card'">
		-->
          <article class="info">
            <div class="name">{{person.fname}} {{person.lname}}</div>
            <div class="birthday">{{person.years}} <span class="year-title"></span></div>
			<div class="age">{{age(person)}} <span class="year-title">years</span></div>
          </article>
          <footer class="footer-card">
            <span class="btn edit">Edit</span>
            <span class="btn remove">Remove</span>
          </footer>
        </section>
      </section>
    </main>
</template>

<script setup>
function age({years}){
	let date = new Date();
	let year = date.getFullYear();
	return year - years;
}
let persons = [
		{
			fname: "Magdalena",
			lname: "Mikulova",
			years: 1993,
		},
		{
			fname: "Mirka",
			lname: "Makovicova",
			years: 2001,
		},
		{
			fname: "Hugo",
			lname: "Hugovic",
			years: 1988,
		},
		{
			fname: "Miki",
			lname: "Hric",
			years: 1920,
		},
		{
			fname: "Andrea",
			lname: "Veresova",
			years: 2020,
		},
		{
			fname: "Nora",
			lname: "Mojsejova",
			years: 1500,
		},
		{
			fname: "Zdenka",
			lname: "Studenkova",
			years: 1,
		}
	]
</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@200;300;500;600;700&display=swap');
	body {
		background: linear-gradient(to bottom, #317773, #0c1e1d);
		background-attachment:fixed;
		background-repeat: no-repeat;
		background-size: cover;
		font-size: 10px;	
		font-family: 'Oswald', sans-serif;
		padding: 1rem;
	}
	main {
		display: flex;
		flex-direction: column;
		gap: .75rem;
	}
	.list {
		display: flex;
		gap: 20px;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: stretch;
		font-size: 1.2rem;
	}
	.card-container {
		flex-grow: 1;
	}
	.card {
		background: linear-gradient(to left, rgba(3, 217, 241, 0.38), rgba(3, 33, 124, 0.46));
		border: 1px solid #bbb;
		color: #444;
		box-shadow: 0 3px 5px rgba(0,0,0,.2);
		border-top-width: 5px;
		border-top-color: rgb(0, 195, 255);
	}
	.card.adult {
		border-top-color: rgba(21, 138, 8, 0.528);
	}
	.card.above50 {
		border-top-color: rgba(255, 213, 0, 0.706);
	}
	.card:hover {
		background: #8AAAE5;
	}
	.info {
		padding: 1rem;
		text-align: center;
		font-size: 1.3rem;
	}
	.name {}
	.age {
		font-weight: 300;
		font-size: 1rem;
	}
	.year-title {
		color: #bbbbbb;
	}
	.footer-card {	
		display: flex;
	}
	.btn {
		padding: .75rem 2rem;
		color: white;
		width: 50px;
		flex-grow: 1;
		text-align: center;
		transition: .5s;
		font-size: 1rem;
	}
	.btn.edit {
		background: #317773;
	}
	.btn.remove {
		background: #99b4f2;
	}
	.btn:hover {
		opacity: .3;
		cursor: pointer;;
	}
</style>