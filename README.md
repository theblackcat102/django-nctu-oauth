# django-nctu-oauth

This package currently still in testing stage
## Setup
1. Register your app at [nctu oauth website](https://id.nctu.edu.tw/)
    Note: you are required to define a redirect urls for accepting the oauth token as well
2. Install package from pip
```
    pip install django-nctu-oauth
```

3. Add package to django project
```
    NCTU_APP_REDIRECT_URI = 'your-redirect-url'
    NCTU_APP_CLIENT_ID = 'your-client-id'
    NCTU_APP_CLIENT_SECRET = 'your-secret-key'

    INSTALLED_APPS = [
        'django-nctu-oauth',
    ]
```
4. Define your redirect views and urls
views.py
```
def oauth(request):
	access_token = request.GET.get('code', None)
	if access_token and oauthWrapper.get_token(request, access_token):
		return redirect('main')
	return HttpResponse("Hello, world. You're at the polls index.")
```
urls.py
```
urlpatterns = [
    ...
    url('oauth', views.oauth, name='oauth'),

]
```

## Testing
```
    python -m test.test
```