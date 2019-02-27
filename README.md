# Android Test Task
The test task involves writing a simplified version of the user's list of savings goals, the list that the user sees when opening the app. This list should be displayed as the provided image shows. Each goal has one entry in the list displaying the goals image, an optional target amount and how much has been saved. See provided image.

## Implementation
We provide you with a simplified API to get the list of goals to display and information about them. The API does not require any login. 
What we would like to see is:
 - A project written ideally in Kotlin but we will accept Java as well
 - some usage of [RxJava](https://github.com/ReactiveX/RxJava)
 - some usage of [Google Databinding](https://developer.android.com/topic/libraries/data-binding/index.html)
 - Read/write data to a persistent storage/DB

How you implement this and what external libraries you use are entirely up to you.

The following API is available:

#### Endpoint
http://qapital-ios-testtask.herokuapp.com

#### /savingsgoals
This resource will return an object with one key, `savingsGoals`. This key maps to a list of goal objects with the following fields:

| Field          | Type	     | Description |
| -------------- | --------- | ----------- |
| goalImageURL   | String    | URL where the image can be downloaded from |
| userId         | Int       | Id of the user that owns this goal |
| targetAmount   | Float     | Target amount of the goal. Might be null |
| currentBalance | Float     | Current balance on the goal. How much has been saved |
| status         | String    | If this goal is active or deleted. A string that is either "active" or "deleted" |
| name           | String    | Name of the goal |
| id             | Int       | Unique id of the goal |
| connectedUsers | List<Int> | A list of user ids that this goal is shared with. |

#### /savingsrules
This resource will return an object with one key, `savingsRules`. This key maps to a list of rules objects with the following fields:

| Field          | Type	     | Description |
| -------------- | --------- | ----------- |
| id             | Int       | Unique id of the rule |
| type           | String    | The type of Savings Rule |
| amount         | Float       | The amount Saving Rule saves |

#### /savingsgoals/:id/feed
This resource will return an object with one key, `feed`. This key maps to a list of feed items for goal details screen:

| Field          | Type      | Description |
| -------------- | --------- | ----------- |
| id             | String    | Unique UUID of the feed event |
| type           | String    | Type of the event |
| timestamp      | String    | Timestamp of event in `YYYY-MM-DDThh:mm:ss+00:00` format |
| message        | String    | Message using HTML syntax  |
| amount         | Float     | Amount saved  |
| userId         | Int       | User id that the event is linked back |
| savingsRuleId  | Int       | Savings Rule id that triggered the event |

#### /users/:id
This resource will return a user object for a specific id. The user object has the following fields:

| Field          | Type   | Description |
| -------------- | ------ | ----------- |
| userId         | Int    | Unique user id |
| displayName    | String | Display name of user |
| avatarUrl      | String | URL where the users avatar can be downloaded from |


## Testing
We expect the task to contain unit tests. UI tests are also welcome.

## Design
There is a sketch file (or two png images) showing how we would like you to display this list. 

## Submiting
Just send us your code along with a description on how to run the app and the tests. If there is anything that you have not had time to complete or intentionally left out please reason on how you would implement it or why it was left out.
