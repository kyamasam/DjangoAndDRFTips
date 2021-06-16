### Setting pagination style
#### In this tutorial, we will implement the PageNumberPagination style
#### Add the following to settings.py 
```
REST_FRAMEWORK = {
    'DEFAULT_PAGINATION_CLASS': 'core.pagination.StandardResultsSetPagination',
    'PAGE_SIZE': 100
}
```

### Adding custom pagination classes

Create a file named pagination.py in one of your apps eg core and the following code:

```
class LargeResultsSetPagination(PageNumberPagination):
    page_size = 1000
    page_size_query_param = 'page_size'
    max_page_size = 10000

class StandardResultsSetPagination(PageNumberPagination):
    page_size = 100
    page_size_query_param = 'page_size'
    max_page_size = 1000
```

To apply a custom pagination class on a class :
```
class BillingRecordsView(generics.ListAPIView):
    queryset = Billing.objects.all()
    serializer_class = BillingRecordsSerializer
    pagination_class = LargeResultsSetPagination
```

If the pagination class is not set, the default pagination will be applied. 

To remove pagination for a specific viewset, add the following code to the viewset
```
pagination_class = None
```


### Accessing a specific page:
Pages can be accessed as follows

```
GET https://api.example.org/accounts/?page=4
```

### Note that is a minified tutorial. To view all available pagination options,  [https://www.django-rest-framework.org/api-guide/pagination/] (view)