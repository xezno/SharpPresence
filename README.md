# SharpPresence
Discord RPC / Rich Presence bindings/wrapper for C#

## Usage

Using SharpPresence is not unlike using the official C SDK.  Simply either compile & add reference to the library in your project, or add the file "Discord.cs".

## Structures

### `EventHandlers`
- ready - the function to be called when the API is ready
- disconnected - the function to be called when Discord has disconnected
- errored - the function to be called when there is an error
- joinGame - the function to be called when a game is to be joined
- spectateGame - the function to be called when a game is to be spectated
- joinRequest - the function to be called when a join request has been recieved

### `RichPresence`
- state (`string`) - the 'state' section of the rich game data
- details (`string`) - the 'details' section of the rich game data
- startTimestamp (`Int64`) - the time at which the game started
- endTimestamp (`Int64`) - the time at which the game will end
- largeImageKey (`string`) - the large image
- largeImageText (`string`) - the large image tooltip
- smallImageKey (`string`) - the small image
- smallImageText (`string`) - the small image tooltip
- partyId (`string`) - the party ID
- partySize (`int`) - the number of players in the party
- partyMax (`int`) - the maximum number of players in the party
- matchSecret (`string`) - the match ID
- joinSecret (`string`) - the match join ID
- spectateSecret (`string`) - the match spectate ID
- instance (`sbyte`) - whether or not the game is a session

### `JoinRequest`

This structure contains:
- userId (`string`): the ID of the user requesting to join
- username (`string`): the username of the user requesting to join
- avatar (`string`): the avatar of the user requesting to join

## Functions

### `Initialize(...)`

This function takes the form of `Discord.Initialize(string, EventHandlers)`.  It is simply a wrapper for `Discord_Initialize(...)` and handles references, among other details.  Currently it does not support the `optionalSteamId` parameter, however it can easily be modified to allow for customizability.

### `UpdatePresence(...)`

This function takes the form of `Discord.UpdatePresence(RichPresence)`.  It handles pointers and memory allocation to wrap `Discord_UpdatePresence(...)` very nicely and help to make code much more readable.

### `Shutdown()`

Does nothing special.  Simply wraps the function `Discord_Shutdown()` within the OOP-focused layout.

### `UpdateConnection()`

Does nothing special.  Simply wraps the function `Discord_UpdateConnection()` within the OOP-focused layout.

### `RunCallbacks()`

Does nothing special.  Simply wraps the function `Discord_RunCallbacks()` within the OOP-focused layout.

### `Respond()`

Does nothing special.  Simply wraps the function `Discord_Respond()` within the OOP-focused layout.

## Enumerations

### `Reply`

The three states recieved from a game after a join request has been sent.

- No
- Yes
- Ignore
