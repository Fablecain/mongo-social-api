# mongo-social-api

This project implements a RESTful API for a social network web application using MongoDB as the database and Express.js for routing. It allows users to share thoughts, react to friends' thoughts, and manage their friend lists.

## Installation

1. Clone this repository.
2. Install dependencies using `npm install`.
3. Set up your MongoDB database.
4. Start the server using `npm start`.

## Usage

- Use Insomnia or any API testing tool to interact with the API endpoints.
- Check the API documentation below for available routes and functionalities.

#### User

- `username`: String (Required, Unique)
- `email`: String (Required, Unique, Valid Email)
- `thoughts`: Array of ObjectIds referencing the Thought model
- `friends`: Array of ObjectIds referencing the User model
- `friendCount`: Virtual field to retrieve the length of the user's friends array

#### Thought

- `thoughtText`: String (Required, 1-280 characters)
- `createdAt`: Date (Default: Current timestamp)
- `username`: String (Required)
- `reactions`: Array of Reaction subdocuments
- `reactionCount`: Virtual field to retrieve the length of the thought's reactions array

#### Reaction (Subdocument Schema)

- `reactionId`: ObjectId (Default: New ObjectId)
- `reactionBody`: String (Required, 280 characters maximum)
- `username`: String (Required)
- `createdAt`: Date (Default: Current timestamp)

#### /api/users

- `GET /`: Get all users
- `GET /:userId`: Get a single user by id with populated thought and friend data
- `POST /`: Create a new user
- `PUT /:userId`: Update a user by id
- `DELETE /:userId`: Delete a user by id

#### /api/users/:userId/friends/:friendId

- `POST /`: Add a new friend to a user's friend list
- `DELETE /`: Remove a friend from a user's friend list

#### /api/thoughts

- `GET /`: Get all thoughts
- `GET /:thoughtId`: Get a single thought by id
- `POST /`: Create a new thought
- `PUT /:thoughtId`: Update a thought by id
- `DELETE /:thoughtId`: Delete a thought by id

#### /api/thoughts/:thoughtId/reactions

- `POST /`: Create a reaction for a thought
- `DELETE /:reactionId`: Remove a reaction by id

## Contributors

- Isaiah LeDuc @Fablecain

## License

This project is licensed under the [MIT License]
