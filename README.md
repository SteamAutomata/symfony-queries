# Tutorials, Fortune Cookies & Doctrine Queries

Ce dépôt contient le code et le script pour les [tutoriels sur les requêtes Doctrine](https://symfonycasts.com/screencast/doctrine-queries) sur SymfonyCasts.

## Configuration
## Setup

Pour le faire fonctionner, suivez ces étapes :

**Télécharger les dépendances de Composer**

Assurez-vous d'avoir [Composer installé](https://getcomposer.org/download/) 
et exécutez ensuite :

```bash
composer install
```

ous devrez éventuellement exécuter php composer.phar install, 
selon comment vous avez installé Composer.

**Configuration de la base de données**

Le code est livré avec un fichier docker-compose.yaml et nous recommandons
d'utiliser Docker pour démarrer un conteneur de base de données. 
PHP sera toujours installé en local, mais vous vous connecterez à une base de données
 à l'intérieur de Docker. C'est facultatif, mais je pense que vous allez l'adorer !

Tout d'abord, assurez-vous d'avoir Docker installé et en cours d'exécution. 
Pour démarrer le conteneur, exécutez :

```
docker compose up -d
```

Next, build the database with:

```
# "symfony console" is equivalent to "bin/console"
# but it's aware of your database container
symfony console doctrine:database:create --if-not-exists
symfony console doctrine:schema:update --force
symfony console doctrine:fixtures:load
```

(If you get an error about "MySQL server has gone away", just wait
a few seconds and try again - the container is probably still booting).

If you do *not* want to use Docker, just make sure to start your own
database server and update the `DATABASE_URL` environment variable in
`.env` or `.env.local` before running the commands above.

**Start the Symfony web server**

You can use Nginx or Apache, but Symfony's local web server
works even better.

To install the Symfony local web server, follow
"Downloading the Symfony client" instructions found
here: https://symfony.com/download - you only need to do this
once on your system.

Then, to start the web server, open a terminal, move into the
project, and run:

```
symfony serve
```

(If this is your first time using this command, you may see an
error that you need to run `symfony server:ca:install` first).

Now check out the site at `https://localhost:8000`

Have fun!

**OPTIONAL: Webpack Encore Assets**

This app uses Webpack Encore for the CSS, JS and image files.
But, the built files are already included... so you don't need
to download or build anything if you don't want to!

But if you *do* want to play with the CSS/JS and build the
final files, no problem. Make sure you have [yarn](https://yarnpkg.com/lang/en/)
or `npm` installed (`npm` comes with Node) and then run:

```
yarn install
yarn encore dev --watch

# or
npm install
npm run watch
```

## Have Ideas, Feedback or an Issue?

If you have suggestions or questions, please feel free to
open an issue on this repository or comment on the course
itself. We're watching both :).

## Thanks!

And as always, thanks so much for your support and letting
us do what we love!

<3 Your friends at SymfonyCasts
