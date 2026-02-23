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

### Deleting Data
```
>>> harry_potter = Book.objects.all()[0]
>>> harry_potter.delete()
(1, {'book_outlet.Book': 1})
>>> Book.objects.all()
<QuerySet [<Book: Lord of the Rings (4)>]>
```

### Create instead of save
```
Book.objects.create(title="Harry Potter 1", rating=5, author="J.K. Rowling", is_bestselling=True)
Book.objects.create(title="Random", rating=2, author="Random", is_bestselling=False)
```

### Querying and filtering
```
-- only returns one result || error
Book.objects.get(id=2)
Book.objects.get(rating=5)
Book.objects.get(is_bestselling=True)

-- can return multiple results
Book.objects.filter(is_bestselling=True)
Book.objects.filter(rating__lte=4)
Book.objects.filter(rating__lte=4, title__contains="Random")
```

### 'or' Condition
```
>>> from django.db.models import Q
>>> Book.objects.filter(Q(rating__lt=3) | Q(is_bestselling=True))
<QuerySet [<Book: Lord of the Rings (4)>, <Book: Harry Potter 1 (5)>, <Book: Random (2)>]>
>>> Book.objects.filter(Q(rating__lt=3) | Q(is_bestselling=True), author="J.K. Rowling")
<QuerySet [<Book: Harry Potter 1 (5)>]>
```

### Query Performance
```
>>> bestsellers = Book.objects.filter(is_bestselling=True)
>>> amazing_bestsellers = bestsellers.filter(rating__gt=4)
>>> print(bestsellers)
<QuerySet [<Book: Lord of the Rings (4)>, <Book: Harry Potter 1 (5)>]>
>>> print(amazing_bestsellers)
<QuerySet [<Book: Harry Potter 1 (5)>]>
```

```
python manage.py createsuperuser
```

```
python manage.py shell
from book_outlet.models import Book
jkrowling = Author(first_name="J.K.", last_name="Rowling")
jkrowling.save()
```
