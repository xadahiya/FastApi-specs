
# HX App
Please read https://hypersonixio.atlassian.net/wiki/spaces/EN/pages/402522249/API+Framework+for+Microservices before gettings started.

## Initializing a cloned repo
When you first clone the repo, you need to run the following commands as part of the initial local setup.
THIS STEP IS NON OPTIONAL.

```
poetry install
```
```
pre-commit install
```

## Building the App
Build the relavant docker images using the command
```
docker-compose build
```

## Starting the App
Start the aapp using

```
docker-compose up
```


## Dependencies
Dependencies are managed using poetry.
Documentation ara available [here](https://python-poetry.org/docs/)

### Adding a package
```
poetry add <package>
```
After adding the package please re build the image.

## Auth Example
Auth plugings are built-in and can be used simply by doing something like this

```
@router.get('/userinfo')
def index(user: Dict = Depends(JWTBearer())) -> Optional[Dict]:

    return {'userinfo': user}
```


## Pagination Example
Pagination support is also built-in using `fastapi_pagination` and can be used by doing something like this
```
@router.get('/users', response_model=Page[User])
async def get_users():
    return paginate(users)
```
See `app/routes` folder for full example. Docs can be found here https://uriyyo-fastapi-pagination.netlify.app/

## Other Features
Other features like APM, logging and health checks are already setup for your convenience. Use .env file to configure things according to your needs.
