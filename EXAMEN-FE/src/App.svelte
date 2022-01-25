<script>
	import { onMount } from 'svelte';
	import Movie from './composant/movie.svelte';

	let movies = [];
	let pagination = {};
	const take=10;
	var skip=0;
	var curentp=1;
	var sp=1;
	var ep=10;	
  //getting data from expressjs project
	async function getMovies(){
		fetch("http://localhost:4000/movies=")
		.then((res) => res.json())
		.then( function(res){
			movies=res.data;
			pagination=res.pagination;
			console.log(movies.length);
		})
		
	}
	//this function call the function getMovies when the component become mounted
	onMount(async function() {
		getMovies();


	});

</script>
*/
<main>
	
	<div class="container-fluid  ml-5 p-5">

<h2 class="header mb-5 fst-italic"> Movies: </h2>
		<table class="table ">
			<thead class="bg-secondary">
			  <tr>
				<th scope="col">title</th>
				<th scope="col">genres</th>
				<th scope="col">year</th>
			  </tr>
			</thead>
			<tbody class="bg-light">
				{#each movies as movie}
			  <tr>
				<td>{movie.title}</td>
				<td><div class=" d-flex " id="c">
					{#each movie.genres as genre}
					<div value="{genre}" class="">{genre} ,</div>
					
					{/each}
				
				</div></td>
				<td>{movie.year}</td>
			  </tr>
			  {/each}
			</tbody>
			
		  </table>
	</div>
	<footer>
		<ul id="cont"></ul>
		</footer>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
	#c , div{
margin : 5px;
	}
</style>