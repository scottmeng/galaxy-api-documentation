# Game

## GET `/game/game-slug/detail`

	curl 'http://localhost:5000/game/mario-bros/detail'

Get details of a game.

	{
		app_url: "http://mariobro.se",
		artwork: { },
		created: "2014-03-04T12:17:46.563Z",
		developer: { },
		icons: "128",
		name: "Mario Bros",
		screenshots: "yes",
		status: "pending",
		slug: "mario-bros",
		videos: "yes",
		id: "c1d61413-2b2a-4752-8519-24f6dc32782f"
	}

## GET `/featured`

	curl 'http://localhost:5000/featured'

Get a list of featured games.

## POST `/featured`

	curl -X POST 'http://localhost:5000/featured' -d '_user=SSA-TOKEN&game=mario-bros&genres=["action"]'

Add a new featured game.

## PUT `/featured`

	curl -X PUT 'http://localhost:5000/featured' -d '_user=SSA-TOKEN&game=mario-bros&genres=["simulation"]'

Change the genre of an existing featured game.

## DEL `/featured`

	curl -X DELETE 'http://localhost:5000/featured' -d '_user=SSA-TOKEN&game=mario-bros'

Remove an existing featured game.

## GET `/genre`

	curl 'http://localhost:5000/genre'

Get the list of genres.

	[
		{
			name: "Action",
			slug: "action"
		},
		{
			name: "Simulation",
			slug: "simulation"
		}
	]

## POST `/genre`

	curl -X POST 'http://localhost:5000/genre' -d 'name=Action&slug=action'

Add a new game genre.

## DEL `/genre`

	curl -X DELETE 'http://localhost:5000/genre' -d 'slug=action'

Remove a game genre.

## GET `/list`

	curl 'http://localhost:5000/game/list?count=2'

Get the list of games matching provided filters.

	[
		{
			app_url: "http://halo.com",
			created: "2014-02-25T08:10:28.617Z",
			icons: "128",
			name: "Halo 718",
			screenshots: "yes",
			slug: "halo-718"
		},
		{
			app_url: "http://mariobro.se",
			created: "2014-03-04T12:17:46.563Z",
			icons: "128",
			name: "Mario Bros",
			screenshots: "yes",
			slug: "mario-bros"
		}
	]

## Game list

## Game moderate

## Game submission

## Leaderboard

# User