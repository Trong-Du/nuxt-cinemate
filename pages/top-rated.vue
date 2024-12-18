<template>
    <div>
        <section>
            <h1 class="text-5xl font-extrabold dark:text-white">Top Rated Movies</h1>
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
        <section>
            <h1 class="text-5xl font-extrabold dark:text-white">Top Rated TV Series</h1>
            <br><br>
            <ul class="grid grid-cols-2 md:grid-cols-5 gap-4">
                <li
                    v-for="tvSeries in series"
                    :key="tvSeries.id"
                >
                    <SeriesCard
                        :poster_path="tvSeries.poster_path"
                        :name="tvSeries.name"
                        :overview="tvSeries.overview"
                        :first_air_date="tvSeries.first_air_date"
                        :popularity="tvSeries.popularity"
                        :item="tvSeries"
                    />
                </li>
            </ul>
        </section>
    </div>
</template>

<script setup>
const movies = useState(() => [])
const series = useState(() => [])
await useFetch('/api/movies/top-rated', {
    transform: data => {
        movies.value = data.topRatedMovies.results
        series.value = data.topRatedSeries.results
    }
})

</script>