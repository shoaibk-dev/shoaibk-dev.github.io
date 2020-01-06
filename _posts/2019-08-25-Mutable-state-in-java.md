---
layout: post
title: Mutable state in java
---

In the following Java example, the BookStore class manages the sale of books in a bookstore, this class includes the member objects for the bookstore inventory and sales database manager classes. The BookStore class includes a method for updating the sales database and inventory when a book is sold. This method retrieves a Book object from the bookstore inventory object using the supplied ISBN number for the book class, then calls a method for the sales object to update the sales information and then calls a method for the inventory object to update inventory for the BookStore.

```
public class BookStore {
private BookStoreInventory inventory;
private SalesDBManager sales;
...
// constructor for BookStore
public BookStore() {
this.inventory = new BookStoreInventory();
this.sales = new SalesDBManager();
...
}
public void updateSalesAndInventoryForBookSold(String bookISBN) {

// Get book object from inventory using ISBN
Book book = inventory.getBookWithISBN(bookISBN);
// update sales information for book sold
sales.updateSalesInformation(book);
// update inventory
inventory.updateInventory(book);
}
// other BookStore methods
...
}
public class Book {
private String title;
private String author;
private String isbn;
// Book object constructors and get/set methods
...
}
```

However, in this example the Book object that is retrieved and passed to the method of the sales object could have its contents modified by the method. This could cause unexpected results when the book object is sent to the method for the inventory object to update the inventory.

In the Java programming language arguments to methods are passed by value, however in the case of objects a reference to the object is passed by value to the method. When an object reference is passed as a method argument a copy of the object reference is made within the method and therefore both references point to the same object. This allows the contents of the object to be modified by the method that holds the copy of the object reference. [REF-374]

In this case the contents of the Book object could be modified by the method of the sales object prior to the call to update the inventory.

To prevent the contents of the Book object from being modified, a copy of the Book object should be made before the method call to the sales object. In the following example a copy of the Book object is made using the clone() method and the copy of the Book object is passed to the method of the sales object. This will prevent any changes being made to the original Book object.

```
...
public void updateSalesAndInventoryForBookSold(String bookISBN) {

// Get book object from inventory using ISBN
Book book = inventory.getBookWithISBN(bookISBN);
// Create copy of book object to make sure contents are not changed
Book bookSold = (Book) book.clone();
// update sales information for book sold
sales.updateSalesInformation(bookSold);
// update inventory
inventory.updateInventory(book);
}
...
```
Pass in data which should not be altered as constant or immutable.

Clone all mutable data before passing it into an external function . This is the preferred mitigation. This way, regardless of what changes are made to the data, a valid copy is retained for use by the class. 
