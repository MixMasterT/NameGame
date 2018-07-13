# NameGame
Name Learning Game Project

## General Gist
* Main screen offers three options (work) / (personal) / (add)
* Work and personal cycle through face images, and require the player to select the correct name from a list
* Alternate game requires the player to select a photo based on a name queue
* Add section allows user to take photo, or paste in image link, and add name to either work or personal
* Cycling through images goes in randomized order to start, but then increases frequency of cards that were misidentified
* Stats will be kept for each user and processed with Elastic for team analysis
* Future versions will have institutional accounts, that allow bulk account generation, and internal use / accuracy metrics.
* Monetize here: 10$ monthly for for-profit institutions. Free for non-profit institutions.
* Platforms - Web -> iOS / Android
* Stack - Vue - Vue / NativeScript - Rails ( Consider node / lambda) - Cloudinary for images

## Dev Plan:
1. Plan DataBase (Finish by 7/20)
			-Institution
				-joins players through TeamMembers (join table)
			-Player
				-name
				-blurb
			-Image
				-playerId (Players can have more than one image)
1. Plan UX (Finish by 7/27)
1. Build Rails Backend
###### Phase 1
**Only one Institution (1904labs) - All players belong to this team only**
  * Basic Authentication (use Devise or Passport) **Allow Google sign-in**
  * Set player's own account (with photo and name)
###### Phase 2
  * To support game, send array of 10 player cards in a random order (API endpoint)
###### Phase 3
	* Add Tables for Game plays, Name Selections, Face Selections
	* Add API endpoint for Player View, showing individuals stats (such as average, total attempts, total games completed...)
	* Add blurb to Player model
	* Add ElasticSearch data store to keep stats
###### Phase 4
	* Allow Institution Creation with bulk sign-up
	* Restrict peer account views to shared Team
	* Add Elastic
###### Phase 5
	* Add payment handling
1. Build Vue Frontend
###### Phase 1
			* Login / Logout
			* Create / Edit Account
###### Phase 2
  * Game 1
    * Cycles through cards in order, showing correct name, plus three bogus names (some of which come from other names in list)
    * Player selects name
    * Give player feedback
    * If wrong, card goes back into array in position 4, else card is removed from array
		* Player wins by eliminating all the cards

  * Game 2
    * Name is shown at top of page, with four face photos below
    * Player chooses face that matches name
    * Player recieves feedback
    * If wrong, name goes to position 4 in queue, else name is discarded from array
		* Win by eliminating all cards
###### Phase 3
		* Add time tracking to game
		* Send post request to Elastic for each selection and record data accordingly
		* Send post request after game is complete to Elastic including time to completion
		* Add Player View so players can view other players Profile (with pic, blurb, and stats)
###### Phase 4
		* Build Team creation interface, and bulk upload process
		* Add Kibana and stat viewing for Institutions/Teams
###### Phase 5
		* Add paid (for-profit) account creation
1. Tool up for Vue / NativeScript
