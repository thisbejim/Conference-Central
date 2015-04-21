# Conference Central

## Explain your design choices

Sessions are created as a child of a Conference, making Profile the ancestor of both. This allows for querying by ancestor which is useful for getting all child elements. typeOfSession was defined as a repeated property to account for multiple possible session types. startTime was defined as a TimeProperty instead of DateProperty to keep entries to 24 hour time and allow for proper filtering.

Speaker was defined as a string in the Session model to make filtering simple.  

## Come up with 2 additional queries

### getWishlistBySpeaker
This query returns all sessions by the same speaker on a user’s wishlist. This would be useful if you are at a conference and see a speaker you enjoy and would like to see more sessions by the same person. 

### getWishlistByType
This query returns all sessions on a user's wishlist of a certain type. This would be useful if you had been to a few presentations and wanted to attend only workshops for the rest of the day.  

## query problem
The problem with trying to query for sessions that are both before 7pm and are not workshops is that the app engine does not allow for two inequality filters to be applied to two seperate properties in one query. In getConferenceSessionsProblem, at first I queried only for sessions before 7pm and then tried to delete results that weren't workshops, but the Query object doesn't allow for deletion. Ultimately I iterated over the time query results and used - 'workshop' not in - to find the results I actually wanted and pass them to a new array.  

## Setup
Download the [App Engine SDK](https://cloud.google.com/appengine/downloads)

Clone this repository

Run the App Engine Launcher and add the Conference Central directory.

Run the launcher on the app and browse to -

http://localhost:[PORT] - application front end

http://localhost:[PORT]/_ah/api/explorer - application API explorer

http://localhost:[ADMIN PORT] - application admin

