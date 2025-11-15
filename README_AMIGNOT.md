## Link to Postman Collection:
> Please open the link below and run the different queries in the Postman standalone app to test code (queries will not execute in web broswer)

https://alainmignot-tech-620246.postman.co/workspace/Alain_SWE's-Workspace~fa3c621a-d4f4-4ba4-84f8-4d2deca5a6f3/collection/49806888-80e192d7-ab9a-4ec3-a468-72e2d1841743?action=share&source=copy-link&creator=49806888

### Here are the individual queries just in case needed:

**booksByAuthorId (valid):**  
AuthorID found returns the author's list of books
```
query {
  booksByAuthorId(authorId: 0) {
    isbn
    title
    authorId
  }
}
```

**booksByAuthorId (invalid):**  
AuthorID not found returns an empty list
```
query {
  booksByAuthorId(authorId: 100) {
    isbn
    title
    authorId
  }
}
```

**booksByTitleSubstring (valid):**  
Substring found in title(s) returns list of books that includes the substring
```
query {
  booksByTitleSubstring(titleSubstring: "The") {
    isbn
    title
    authorId
  }
}
```

**booksByTitleSubstring (invalid):**  
Substring not found in any titles returns an empty list
```
query {
  booksByTitleSubstring(titleSubstring: "abc123xyz456") {
    isbn
    title
    authorId
  }
}
```

**authorsByLastName (valid):**  
Last name found returns a list of authors with that last name
```
query {
  authorsByLastName(lastName: "Frost") {
    id
    firstName
    lastName
  }
}
```

**authorsByLastName (invalid):**  
Last name not found returns empty list
```
query {
  authorsByLastName(lastName: "Jones") {
    id
    firstName
    lastName
  }
}
```

**updateAuthorLastname (valid):**  
Valid query updates an author's last name by id and returns old name
```
mutation {
  updateAuthorLastName(id: 0, newLastName: "Frostman") {
    oldLastName
  }
}
```

**updateAuthorLastName (invalid):**  
Invalid request returns null for oldLastName
```
mutation {
  updateAuthorLastName(id: 100, newLastName: "Stevens") {
    oldLastName
  }
}
```

**deleteBook (valid):**  
Valid request deletes the book and returns the isbn of deleted book
```
mutation {
  deleteBook(isbn: "123456789") {
    isbn
  }
}
```

**deleteBook (invalid):**  
Isbn not found returns null for deleting a book
```
mutation {
  deleteBook(isbn: "5555555") {
    isbn
  }
}
```

**booksByAuthorFirstName (valid):**  
Valid query returns list of books by author(s) with a given first name
```
query {
  booksByAuthorFirstName(firstName: "Robert")
}
```

**booksByAuthorFirstName (invalid):**  
Invalid first name returns an empty list
```
query {
  booksByAuthorFirstName(firstName: "Michael")
}
```