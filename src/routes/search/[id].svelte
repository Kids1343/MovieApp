<script context="module">
    export async function load({fetch, params}){
        const res = await fetch(`https://api.themoviedb.org/3/movie/${params.id}?api_key=<<api_key>>&language=en-US`);
        const movieDetail = await res.json();
        if(res.ok){
            return{
                props: {searchedMovie: movieDetail}
            }
        }
    }   
</script>

<script>
    import MovieCard from "../../components/MovieCard.svelte";
    export let searchedMovie;
</script>

<div class="searched-movies">
    {#each searchedMovie as movie}
        <MovieCard {movie} />
    {/each}
</div>