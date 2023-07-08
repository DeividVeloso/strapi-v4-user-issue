
## Install POstgress on your local machice

Login on postgress
```
psql -U postgres

```

## Create a user
```
CREATE USER test WITH ENCRYPTED PASSWORD 'test123';
```

## create the database
```
CREATE DATABASE testdb OWNER test;
```

## Run the project

```
yarn 
yarn develop
```

## Open Admin Panel
Create a user 
Create some games

## Open the Graphql Playground

```
http://localhost:1337/graphql
```

## Mutations

### Login

```
mutation Login($input: UsersPermissionsLoginInput!) {
  login(input: $input) {
    jwt,
    user {
      username
      email
    }
  }
}


{
  "input": {
    "identifier": "lula@gmail.com",
    "password": "********"
  }
}
```

### Wishlist Create

```
mutation MutationCreateWishlist($data: WishlistInput!) {
  createWishlist(data: $data) {
    data {
      id
      attributes {
        user {
          data {
            attributes {
              username
              email
              provider,
              role {
                data {
                  attributes {
                    name
                  }
                }
              }
            }
          }
        }
        games {
          data {
            attributes {
             name
            }
          }
        }
      }
    }
  }
}


HTTP HEADERS

{
  "Authorization": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9......."
}

Query Variables

{
  "data": {
    "user": 1,
    "games": ["1", "2"]
  }
}
```

You should get an error of `Forbidden access`, however the data was successfully create on the database.
