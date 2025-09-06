# 5e-database-ru
Форк для перевода 5e-database на русский язык.

Переводы хранятся в ветке `translated`.

### Прогресс:
2014:
- [ ] `0%` 5e-SRD-Ability-Scores.json
- [ ] `0%` 5e-SRD-Alignments.json
- [ ] `0%` 5e-SRD-Backgrounds.json
- [ ] `0%` 5e-SRD-Classes.json
- [ ] `0%` 5e-SRD-Conditions.json
- [ ] `0%` 5e-SRD-Damage-Types.json
- [ ] `0%` 5e-SRD-Equipment-Categories.json
- [ ] `0%` 5e-SRD-Equipment.json
- [ ] `0%` 5e-SRD-Feats.json
- [ ] `0%` 5e-SRD-Features.json
- [ ] `0%` 5e-SRD-Languages.json
- [ ] `0%` 5e-SRD-Levels.json
- [ ] `0%` 5e-SRD-Magic-Items.json
- [ ] `0%` 5e-SRD-Magic-Schools.json
- [ ] `0%` 5e-SRD-Monsters.json
- [ ] `0%` 5e-SRD-Proficiencies.json
- [ ] `0%` 5e-SRD-Races.json
- [ ] `0%` 5e-SRD-Rule-Sections.json
- [ ] `0%` 5e-SRD-Rules.json
- [ ] `0%` 5e-SRD-Skills.json
- [x] `90%` 5e-SRD-Spells.json
- [ ] `0%` 5e-SRD-Subclasses.json
- [ ] `0%` 5e-SRD-Subraces.json
- [ ] `0%` 5e-SRD-Traits.json
- [ ] `0%` 5e-SRD-Weapon-Properties.json

2024:
- [ ] `0%` 5e-SRD-Ability-Scores.json
- [ ] `0%` 5e-SRD-Alignments.json
- [ ] `0%` 5e-SRD-Conditions.json
- [ ] `0%` 5e-SRD-Damage-Types.json
- [ ] `0%` 5e-SRD-Languages.json
- [ ] `0%` 5e-SRD-Magic-Schools.json
- [ ] `0%` 5e-SRD-Skills.json
- [ ] `0%` 5e-SRD-Weapon-Mastery-Properties.json
- [ ] `0%` 5e-SRD-Weapon-Properties.json

# Сборка/использование образа

- Соберите докер образ (или наполните свою БД через скрипт, инструкция по наполнению данными ниже)
- Опублкуйте образ в DockerHub или GitHub Container Registry
- ### DockerHub
  - Залогиньтесь в Docker Hub: `docker login`
  - Переименуйте образ для публикации: `docker tag 5e-database-ru <ваш_логин>/<имя_образа>:latest`
  - Отправьте образ в репозиторий: `docker push <ваш_логин>/<имя_образа>:latest`
  - Используйте образ:
    - `docker pull <ваш_логин>/<имя_образа>:latest`
    - `docker run -d --name 5e-database-ru -p 27017:27017 <ваш_логин>/<имя_образа>:latest`
- ### GitHub Container Registry
  - Войдите в GHCR: `echo $CR_PAT | docker login ghcr.io -u USERNAME --password-stdin`
  - Переименуйте образ: `docker tag 5e-database-ru ghcr.io/USERNAME/5e-database-ru:latest`
  - Отправьте образ: `docker push ghcr.io/USERNAME/5e-database-ru:latest`
  - Используйте образ:
    - `docker pull ghcr.io/USERNAME/5e-database-ru:latest`
    - `docker run -d --name 5e-database-ru -p 27017:27017 ghcr.io/USERNAME/5e-database-ru:latest`

---

# 5e-database

![Build Status](https://github.com/5e-bits/5e-database/workflows/5e%20Database%20CI/badge.svg?branch=main)
[![Discord](https://img.shields.io/discord/656547667601653787)](https://discord.gg/TQuYTv7)

Holds the database for the D&D 5th Edition API at http://dnd5eapi.co/

Talk to us [on Discord!](https://discord.gg/TQuYTv7)

## How to run

### With Docker

You should be able to build locally and then run the local Docker image. This can be done one of two ways:

1. If you just need an image and you aren't running an M1:

```bash
docker run ghcr.io/5e-bits/5e-database:latest
```

2. If you're running an M1 or you want to test changes that you've made to the Database:

```bash
docker build -t 5e-database .
docker run -i -t 5e-database:latest
```

### Without Docker

First you need to make sure you have [MongoDB installed locally.](https://docs.mongodb.com/manual/installation/)

You can load this data locally by running:

```bash
MONGODB_URI=mongodb://localhost/5e-database npm run db:refresh
```

## API Issues

If you see anything wrong with the API and not the data, please open an issue or PR over [here](https://github.com/5e-bits/5e-srd-api).

## Contributing

* Fork this repository
* Create a new branch for your work
* Push up any changes to your branch, and open a pull request. Don't feel it needs to be perfect — incomplete work is totally fine. We'd love to help get it ready for merging.
* We use Semantic Release so here are the PR naming convetions:

| Commit message                                                                                                                                                                             | Release type                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| fix(pencil): stop graphite breaking when too much pressure applied                                                                                                                         | Patch Fix Release                                                                                        |
| feat(pencil): add 'graphiteWidth' option                                                                                                                                                   | Minor Feature Release                                                                                    |
| perf(pencil): remove graphiteWidth option<br><br>BREAKING CHANGE: The graphiteWidth option has been removed.<br>The default graphite width of 10mm is always used for performance reasons. | Major Breaking Release<br><br>(Note that the BREAKING CHANGE: token must be in the footer of the commit) |

## Code of Conduct

The Code of Conduct can be found [here.](https://github.com/5e-bits/5e-database/wiki/Code-of-Conduct)

## License

This project is licensed under the terms of the MIT license. The underlying material
is released using the [Open Gaming License Version 1.0a](https://www.wizards.com/default.asp?x=d20/oglfaq/20040123f)

## Contributors

<a href="https://github.com/5e-bits/5e-database/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=5e-bits/5e-database" />
</a>
