```
python manage.py shell
```

### Inserting Data
```
>>> from book_outlet.models import Book
>>> harry_potter = Book(title="Harry Potter 1 - The Philosopher's Stone", rating=5)
>>> harry_potter.save()
>>> lord_of_the_rings = Book(title="Lord of the Rings", rating=4)
>>> lord_of_the_rings.save()
```

### Geting All Entries
```
>>> Book.objects.all()
<QuerySet [<Book: Book object (1)>, <Book: Book object (2)>]>
```

### Updating Data
```
>>> from book_outlet.models import Book
>>> Book.objects.all()[1].author
>>> Book.objects.all()[1].is_bestselling
False
>>> harry_potter = Book.objects.all()[0]
>>> harry_potter.title
"Harry Potter 1 - The Philosopher's Stone"
>>> lord_of_the_rings = Book.objects.all()[1]
>>> lord_of_the_rings.title
'Lord of the Rings'
>>> harry_potter.author = "J.K. Rowling"
>>> harry_potter.is_bestselling = True
>>> harry_potter.save()
>>> harry_potter = Book.objects.all()[0]
>>> harry_potter.author
'J.K. Rowling'
>>> lord_of_the_rings.author ="J.R.R. Tolkien"
>>> lord_of_the_rings.is_bestselling = True
>>> lord_of_the_rings.save()
>>> Book.objects.all()[1].author
'J.R.R. Tolkien'
```
