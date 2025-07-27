Queries and explanations 

mongosh - to run data 

show dbs - this will show all existing database

create queries //

use library — This command switches to the database named library. If it doesn't exist, MongoDB will create it when a document is first inserted.

db.createCollection("books") — Explicitly creates a new collection named books. MongoDB automatically creates collections on the first insert, so this step is optional but good practice for structure.

db.books.insertOne({
  title: "The Great Gatsby",
  author: "F. Scott Fitzgerald",
  published_year: 1925
}) — insertOne() is used to insert only one document into the collection. Ideal when you're adding a single book or record.

db.books.insertMany([
  {
    title: "1984",
    author: "George Orwell",
    published_year: 1949
  },
  {
    title: "The Catcher in the Rye",
    author: "J.D. Salinger",
    published_year: 1951
  }
]) — insertMany() allows inserting multiple documents at once, which is more efficient for bulk data entry.

read queries // 

db.books.find() - Returns all documents from the books collection.

db.books.find({ author: "J.K. Rowling" }) — Filters documents where the author matches exactly "J.K. Rowling".

db.books.find().sort({ published_year: 1 }).limit(1) — Sorts the books by published_year in ascending order (1) and limits the output to just 1 result.


Update queries // 

db.books.updateOne(
  { title: "The Catcher in the Rye" },
  { $set: { published_year: 2024 } }
) — updateOne() is used to update the first matching document. $set modifies only the specified field without overwriting the entire document.

db.books.updateMany({},
  { $set: { genre: "Mystery" } }) — updateMany() updates all documents that match the condition. Here, {} matches all documents, and a new genre field is added to each.

Delete queries //

db.books.deleteOne({ title: "1984" }) — deleteOne() deletes the first document that matches the filter. Good for deleting a unique item.

db.books.deleteMany({ published_year: { $lt: 2000 } }) — deleteMany() removes all documents where the published_year is less than 2000. $lt means "less than".

Advanced queries //

db.books.find().sort({ published_year: -1 }).limit(3) — Sorts by published_year in descending order (-1) and returns the top 3 results.


Create	insertOne(), insertMany()	Add new documents
Read	find(), sort(), limit()	Retrieve documents
Update	updateOne(), updateMany()	Modify existing documents
Delete	deleteOne(), deleteMany()	Remove documents


