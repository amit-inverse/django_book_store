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
