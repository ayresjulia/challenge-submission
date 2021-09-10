# Structure API endpoints

## What streaming providers & provider plans have a specific channel?

ANSWER: make a relationship between provider_plans table and channels table THROUGH provider_plan_channels table, so searching for (let's say) espn.channels (with id=9) would result in espn and espn2 from channels table name column. So, when searching for provider_id, user will see available plans and channels. to Include provider plans, return provider name column with the query to get provider ID.

ENDPOINT + method: GET /providers/:providerId

## What provider has a specific upcoming live event?

ANSWER: on click of the channel from a provider, user gets rerouted to channel id page where they can see all events for that channel. The relationship is between channels table and events table THROUGH events_channels table. if asked for  channel id=2, it will show eventid 1 and 2 names, which are US open and MLB
ENDPOINT + method: GET /channels/:id/events then on click of event, GET /events/:id */

## Structure of classes

* class Providers with following static functions (but not limited to):
create(data) where data gets inserted into db
getAll(searchFilters)
get(id) -> this function would join table providers and provider_plans
update(id, data)
delete(id)

* class Channels with following static functions (but not limited to):
create(data) where data gets inserted into db
getAll(searchFilters)
get(id) -> this function would join table channels and events
update(id, data)
delete(id)

* class Users with following static functions (but not limited to, also functiond  strictly available for admins, this would get noted inside the routes, not in classes):
create(data) where data gets inserted into db
getAll(searchFilters)
get(username) -> this function would get user info and perhaps show subscriptions/saved providers
update(username, data)
delete(username)