# Bug-Report

Welcome to the BugReport! 

You have been tasked with creating a tool to better report bugs for your team. The goal being, to better track bugs in your application, as well as the process taken to solve them.

All bugs will have a title, description, who reported the bug, and whether or not it has been closed. 

Users can also notes on the bugs to provide better clarification of the problem.

Once a bug has been closed, there can be no further editing of the report.

Here are some mock-ups from the client
<hr>

### Home View:
<div>
  <img class="img-responsive" src="Home.jpg" />
</div>

From the Home page users can view all the bugs that have been added, color coded to which are open and closed.

#### Challenges 
Try to implement pagination here, as well as being able to sort by the status or the reported date.
<br>
<br>
<hr>


### Details View:
<div>
  <img class="img-responsive" src="Details.jpg" />
</div>

The details view provides some additional information about the bug, as well as showing all the comments made by other users. Here comments can be deleted and added as well. 

#### Challenges:
 See if you can implement the ability to go next or previous from this page.


<hr>
<br>
<br>

## Bug-Report API


### Bug Schema
```Javascript
var bug = new Schema({
    open: { type: Boolean, required: true, default: true },
    description: { type: String, required: true },
    title: { type: String, required: true },
    creator: { type: String, required: true } //The provided name for who reported the bug
    user: { type: String, required: true }
}, { timestamps: true })
```

### Note Schema
```Javascript
var note = new Schema({
    content: { type: String, required: true },
    bug: { type: ObjectId, ref: 'Bug' required: true },
    creator: { type: String, required: true } //The provided name for who made the note
    user: { type: String, required: true }
}, { timestamps: true })
```


### Endpoints
> baseUrl: `'https://bcw-sandbox.herokuapp.com/api/YOURNAME'`

Get

`/bugs`: returns list of bugs for the user

`/bugs/:id`: returns a single bug with all it's data

`/bugs/:id/comments`: returns all comments for a given bug id

Post

`/bugs`: Creates a new bug

`/bugs/:id/notes`: Adds a new note to the bug. *This can only be done if bug is open*

Put 

>*both of these can only be done if bug is open*

`/bugs/:id`: Edits bug

`/bugs/:id/notes/:id`: Edits note.

Delete

> There is no true bug delete, only changing the status of a bug to closed.

`/bugs/:id`: Changes status of bug from open to close

`/bugs/:id/notes/:id`: Deletes note.


<hr>

## Requirements

### Visualization
- At least 2 supported routes
    - Home shows all bugs
    - Details displays the details of a bug and its comments
- Styling Indication on main page that bug is closed (color, strike-through, etc.)
- No option to 'add note' once bug is closed

### Functionality
- Bugs can be created and marked complete
- Notes can be added and removed from a bug
- Utilize the Route Params to retain bug details page on refresh