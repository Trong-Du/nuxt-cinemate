<template>
    <div>
        <section>
            <h1 class="text-5xl font-extrabold dark:text-white">Now Playing Movies</h1>
            <br><br>
            <ul class="grid grid-cols-2 md:grid-cols-5 gap-4">
                <li
                    v-for="movie in movies"
                    :key="movie.id"
                >
                    <MovieCard
                        :poster_path="movie.poster_path"
                        :title="movie.title"
                        :id="movie.id"
                        :overview="movie.overview"
                        :release_date="movie.release_date"
                        :popularity="movie.popularity"
                        :item="movie"
                    />
                </li>
            </ul>
        </section>
    </div>
</template>

<script setup>
const movies = useState(() => [])
await useFetch('/api/movies/now-playing', {
    transform: data => {
        movies.value = data.nowPlayingMovies.results
    }
})
</script>