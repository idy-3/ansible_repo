# Django and React ansible deployment template

This deployment template is mostly following, [Django deployment gist summarized by Brad Traversy](https://gist.github.com/bradtraversy/cfa565b879ff1458dba08f423cb01d71), which in turn is following this [Digital Ocean tutorials](https://www.digitalocean.com/community/tutorials/how-to-set-up-django-with-postgres-nginx-and-gunicorn-on-ubuntu-18-04).
Basically, those two resources should give you, what you need to get this working for you.

## Assumptions

- You have ansible installed on your local system.
- This is assuming that you are using a one server for fronend/backend/database/etc...
- A "Debian" based system.
- A Postgres database.
- Nginx and Gunicorn server.
- An SSH authentication registered with github for ansible to use.
- Rsync installed (Using Rsync to push files to server).

Obviously, modify as meets your needs.

## Instructions

Ensure you have **modified** the places marked with angle brackets **< EDIT HERE >** as meets your unique needs within the files before running the command below.

### Create ansible user, add ssh "authorized_key" and add user to sudoer's

This is just the initial setup, the "bootstrap.yml" playbook. It sets-up a user which ansible will use subsequently to talk to the remote server.
This SSH

```
# ansible-playbook --ask-become-pass bootstrap.yml
```

### Deploy to server

This deploys your app, largely following the deployment instructions given in the guides linked above. It uses the remote user created by the **bootstrap.yml** playbook to talk with the server. Again update the roles to meet your specific use case.

```
# ansible-playbook site.yml
```

Okay, that's it. cheers.
