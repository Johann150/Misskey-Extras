WARNING: THIS IS IRREVERSIBLE AND MAY CAUSE THE SERVER TO CRASH; DO THIS AT YOUR OWN RISK

## Initial Steps
Connect to your PostgreSQL with `sudo -u postgres psql` for example.
With the command `\du` you can Check, which databses you have.

### Now connect to your Misskey-Database
```
\c '{misskey_database}'
```

## Sort the Data you need

You can get the userID from the Server Admin UI.
('Instance' -> 'Users' -> Click on a User and get the ID).

We will use the "AND id" here, cause we will run into Problems, if there are more Users with the same Username on different Instances.

It seeems that, there is nothing in signin, when the user didn't logged in for a while.

```
SELECT * FROM public.used_username WHERE username='{username}}';

SELECT * FROM public.user WHERE username='{username}' AND id='{userId}}';

SELECT * FROM public.signin WHERE userId='{userId}';
```


## Delete the User

So if we got all the Data together, we need. We can delete the User

```
DELETE FROM public.used_username WHERE username='{username}';

DELETE FROM public.user WHERE username='{username}' AND id='{userId}';

DELETE FROM public.signin WHERE userId = '{usedID}';
```


## Inspired By @aho@rosehip.moe
https://cirrostrat.org/blog/2021/07/03/Remove-Used-Usernames-from-Misskey-PSQL-Database/