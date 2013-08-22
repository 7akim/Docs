---
layout: post
title: Overview & Basics
---
This documention is about Google+'s **internal** API.

With the API, you can read & write user's private stream, posts, photos, events, even communities.
So please **respect the privacy of others.** This is very important.

The API may change anytime, I will update this documention as quickly as I can.

Thanks: [@acgotaku](https://github.com/acgotaku) [@lordfriend](https://github.com/lordfriend) [@zh99998](https://github.com/zh99998) And all my friends on Google+.

API Basics
----------
All APIs are based on HTTP/1.1

The base URL is:

		https://www.googleapis.com/plusi/v2/ozInternal/{method}

Only POST request is allowed.

You should always send a Bearer Authorization header. For more details see [Authorization](/apis/auth.html)

Common Fields
-------------
You should always add a "commonFields" property to your JSON request body (including batch requests).

The content of common fields is:
```json
	{
		"appVersion":410508092,
		"appVersionFull":{
			"major":4,
			"minor":1,
			"patch":0
		},
		"socialClient":{
			"application":"GPLUS",
			"device":"ANDROID_TABLET",
			"platform":"NATIVE"
		}
	}
```
You can just simply copy the code above. Do not modify aything, I will update the code when API changed.

API Overview
------------
### Universual & Settings
|Method      |Description                                                                   |
|------------|------------------------------------------------------------------------------|
|searchquery |Query(search) posts,users,etc.                                                |
|postactivity|Post anything(text, URL, location, emotion,etc.) to anywhere(Stream,Community)|
|getmobilesettings|Get the user's mobile APP settings and some basic infomation (Default ACL, display name,email address, profile photo and pages). Useful if you want to post an activity or access the pages that the user managed.|

### Users & Pages
|Method          |Description                                                                   |
|----------------|------------------------------------------------------------------------------|
|getsimpleprofile|Get an user's basic infomation(including public and privite but visible to the current user) and relationship with the user.|
|people/me[v2whitelisted] |Get the current user's simple infomation(avatar, ID and display name)|
|people/me/people/pages[v1whitelisted] |Get the pages that the current user manages.            |
|people/me/applications/connected[v1whitelisted] |Get the current user's connected applications.|
|getreviewsdata  |Get an user's Google Maps review data.                                        |
|muteuser        |Mute or unmute an user.                                                       |
|blockuser       |Block or unblock an user.                                                     |
|mutateprofile   |Modify the current user's personal infomation                                 |

### Activities & Comments
**Activity = Post (including community post), location, event,etc.**

|Method              |Description                                              |
|--------------------|---------------------------------------------------------|
|getactivities       |Get some activities from Stream, an user, or a community.|
|getactivitiesbyid   |Get some activites by their update ID.                   |
|plusone             |+1 anything that we can +1                               |
|getplusonepeople    |Get the list of people that +1'd something.              |
|postcomment         |Post a comment.                                          |
|editcomment         |Modify a comment.                                        |
|deletecomment       |Delete a comment.                                        |
|muteactivity        |Mute an activity.                                        |
|deleteactivity      |Delete an activity.                                      |
|getengagementsummary|Get activities on an activity                            |

### Notifications : TBD.

### Circles & People
|Method              |Description                                              |
|--------------------|---------------------------------------------------------|
|loadsocialnetwork   |Get the current user's social network.                   |
|loadblockedpeople   |Get the users that current user blocked.                 |
|modifymemberships   |Modify the current user's circles.                       |

### Squares & Communities
|Method              |Description                                                                       |
|--------------------|----------------------------------------------------------------------------------|
|getsquares          |Get the communities that the current user's joined, invited,suggested communities.|
|getviewersquare     |Get a community's basic infomation.                                               |
|editsquaremembership|Join or exit an community.                                                        |

### Events
**Events can be created like an activity.**

|Method              |Description                                      |
|--------------------|-------------------------------------------------|
|eventread           |Get an event by querying its ID.                 |
|eventshome          |Get all the events that the current user can see.|
|eventrespond        |Respond an event.                                |
|geteventinviteelist |Get an event's invitee list.                     |

### Photos & Albums : TBD.
