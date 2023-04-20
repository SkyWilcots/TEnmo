
# Module 2 Capstone - TEnmo

## Use cases

### Required use cases

You should attempt to complete all of the following required use cases.

1. As a user of the system, I need to be able to register myself with a username and password.
   1. The ability to register has been provided in your starter code.
2. As a user of the system, I need to be able to log in using my registered username and password.
   1. Logging in returns an Authentication Token. I need to include this token with all my subsequent interactions with the system outside of registering and logging in.
   2. The ability to log in has been provided in your starter code.
3. As a user, when I register a new account is created for me.
   1. The new account has an initial balance of $1000.
4. As an authenticated user of the system, I need to be able to see my Account Balance.
5. As an authenticated user of the system, I need to be able to *send* a transfer of a specific amount of TE Bucks to a registered user.
   1. I should be able to choose from a list of users to send TE Bucks to.
   2. I must not be allowed to send money to myself.
   3. A transfer includes the User IDs of the from and to users and the amount of TE Bucks.
   4. The receiver's account balance is increased by the amount of the transfer.
   5. The sender's account balance is decreased by the amount of the transfer.
   6. I can't send more TE Bucks than I have in my account.
   7. I can't send a zero or negative amount.
   8. A Sending Transfer has an initial status of *Approved*.
6. As an authenticated user of the system, I need to be able to see transfers I have sent or received.
7. As an authenticated user of the system, I need to be able to retrieve the details of any transfer based upon the transfer ID.

Validate all of the API's endpoints using Postman and/or Swagger


## How to set up the database

Create a new Postgres database called `tenmo`. Run the `database/tenmo.sql` script in pgAdmin to set up the database that you'll begin to work from. You should make structure changes in this script and not the database directly. Additionally, both you and your team members need to run this script each time after making changes to it. 

## Database schema

The following tables are created by the provided `tenmo.sql` script. 

### `tenmo_user` table

Stores the login information for users of the system.

| Field           | Description                                                                    |
| --------------- | ------------------------------------------------------------------------------ |
| `user_id`       | Unique identifier of the user                                                  |
| `username`      | String that identifies the name of the user; used as part of the login process |
| `password_hash` | Hashed version of the user's password                                          |

### `account` table

Stores the accounts of users in the system.

| Field           | Description                                                        |
| --------------- | ------------------------------------------------------------------ |
| `account_id`    | Unique identifier of the account                                   |
| `user_id`       | Foreign key to the `tenmo_user` table; identifies user who owns account |
| `balance`       | The amount of TE bucks currently in the account                    |
