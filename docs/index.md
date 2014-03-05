# Game

## GET `/game/GAME-SLUG/detail`

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

	curl 'http://localhost:5000/game/list'

	curl 'http://localhost:5000/game/list?_user=00000000&count=10&status=approved'

Get the list of games matching provided filters.

> Optional parameters:

> `_user`: user id or user slug (only needed for status filter)

> `count`: maximum number of games to return

> `status`: filter by status of game (`approved`, `pending`, `rejected`) 

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

## GET `/game/GAME-SLUG/STATUS`

	curl http://localhost:5000/game/mario-bros/approve'

	curl http://localhost:5000/game/mario-bros/reject'

Change a game to specified status.

> `STATUS`: `approve`, `pending`, `reject`, `disable`, `delete`

## POST `/game/submit`

	curl -X POST 'http://localhost:5000/game/submit' -d 'name=Mario Bros&app_url=http://mariobro.se&icons=128&screenshots=yes'

Submit a game.

## GET `/game/GAME-SLUG/board`

	curl 'http://localhost:5000/game/mario-bros/board'

Return the list of available leaderboards for a game.

	[
		{
			name: "Most Points",
			slug: "most-points",
			data: []
		},
		{
			name: "Most Combo",
			slug: "most-combo",
			data: []
		}
	]

## POST `/game/GAME-SLUG/board`

	curl -X POST 'http://localhost:5000/game/mario-bros/board' -d 'name=Warios Smashed&slug=warios-smashed'

Create a leaderboard for a game.

## DEL `/game/GAME-SLUG/board`

	curl -X DELETE 'http://localhost:5000/game/mario-bros/board' -d 'slug=warios-smashed'

Delete a leaderboard from a game.

## GET `/game/GAME-SLUG/board/BOARD-SLUG`

	curl 'http://localhost:5000/game/mario-bros/board/warios-smashed'

	curl 'http://localhost:5000/game/mario-bros/board/warios-smashed?sort=asc&friendsOnly=true&_user=SSA-TOKEN'

Return the list of scores for a leaderboard of a game.

> Optional parameters:

> `sort`: the order in which the list of scores will be sorted. The default order is descending. (`asc`)

> `friendsOnly`: only show scores of friends (`true`, `false`)

> `_user`: user id or user slug

> `page`: page index for pagination (integer)

> `limit`: number of results per page for pagination (integer)

## PUT `/user/profile`

	curl -X PUT 'http://localhost:5000/user/profile?_user=ssatoken'

Update user profile.

## POST `/user/purchase`

	curl -X POST 'http://localhost:5000/user/purchase' -d '_user=jon-snow&game=mario-bros'

Record user's game purchase.

> Parameters:

> `_user`: user id or username slug

> `game`: game id or game slug

## GET `/user/search`

	curl 'http://localhost:5000/user/search?_user=SSA-TOKEN'

	curl 'http://localhost:5000/user/search?_user=SSA-TOKEN?email=mario@bros.com'

Search for users with email, id or username slug.

> Optional parameters (at least one of them needs to be specified):

> `email`: user email to search for

> `id`: user id to search for

> `devSlug`: developer/company slug to search for

> `q`: email/user id/username to search for

## GET `/user/friends`

	curl 'http://localhost:5000/user/friends?_user=SSA-TOKEN'

Return a list of user's friends.

> Opetional parameters:

> `only`: friend status (`online`, `played`, `playedOnline`, `playing`)

> `game`: game id or game slug

## POST `/user/friends/request`

	curl -X POST 'http://localhost:5000/user/friends/request' -d '_user=SSA-TOKEN&recipient=UID'

Send friend request to a specified user.

> Parameter:

> `recipient`: the user id of friend request recipient

## GET `/user/friends/requests`

	curl 'http://localhost:5000/user/friends/requests?_user=SSA_TOKEN'

Return a list of friend requests for the user.

## POST `/user/friends/ACTION`

	curl -X POST 'http://localhost:5000/user/friends/accept' -d '_user=SSA-TOKEN&acceptee=UID'

	curl -X POST 'http://localhost:5000/user/friends/ignore' -d '_user=SSA-TOKEN&acceptee=UID'

Accept a friend request from a user.

> `ACTION`: `accept`, `ignore`

> Parameter:

> `acceptee`: the user id of a user who sent a friend request to the user

## POST `/user/friends/unfriend`

	curl -X POST 'http://localhost:5000/user/friends/unfriend' -d '_user=SSA-TOKEN&exfriend=UID'

Unfriend a friend.

> Parameter:

> `exfriend`: the user id of a user with whom the user wants to unfriend

## POST `/user/acl`

	curl -X POST 'http://localhost:5000/user/acl' -d '_user=SSA-TOKEN&id=1&dev=1&reviewer=1&admin=1'

Update the permission of a user.

> Parameters:

> `_user`: user's SSA token __[required]__

> `id`: user id to change permission for __[required]__

> `dev`: whether or not user should have developer permission (`0`, `1`) __[required]__

> `reviewer`: whether or not user should have reviewer permission (`0`, `1`) __[required]__

> `admin`: whether or not user should have admin permission (`0`, `1`)

## POST `/user/login`

	curl -X POST 'http://localhost:5000/user/login' -d 'assertion=&audience'

Sign in via Persona.

> Parameter:

> `assertion`: persona assertion
	