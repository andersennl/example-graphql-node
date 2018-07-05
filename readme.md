## Graphql server running on node and json server

### Project description
This project uses `nodemon, express and express-graphql` to run a local GraphQL server. It uses `json-server` to provide a local backend, which uses the local file `data.json` as a local database.

### Setup

Run `yarn` to install the project's dependencies.

Create local JSON database:

`touch data.json`

It will be used by json-server.

### Start
run `npm run json:server`

and

run `npm run dev:server`

Open [http://localhost:4000/graphql](http://localhost:4000/graphql)

### Schema used for this project
```
const CustomerType = new GraphQLObjectType({
  name: "Customer",
  fields: () => ({
    id: {type: GraphQLString},
    name: {type: GraphQLString},
    email: {type: GraphQLString},
    age: {type: GraphQLInt},
  })
});
```

### Example queries
In the GraphiQL web interface (Open [http://localhost:4000/graphql](http://localhost:4000/graphql)), you can use the following example queries.

#### Query all customers, get fields id, name and age

```
{
  customers {
    id
    name
    age
  }
}
```

#### Query specific customer by id, get fields name, email and age
```
{
  customer(id: "NfwMj53") {
    name
    email
    age
  }
}

```

#### Add customer
```
mutation {
  addCustomer(name:"new customer", email:"email@gmail.com", age: 32) {
    id
    name
    age
  }
}
```

#### Delete customer
```
mutation {
  deleteCustomer(id:"Ww911Tg"){
    name
    id
  }
}
```
