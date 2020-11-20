# Getting Started: Development Setup

This document guides you through setting up a proper development environment for the repositories at github.com/waarzitjenu.

---

## Step 1: Clone all repositories in one directory 

The best way to have a local development setup is by making a new directory, like `~/GitHub/waarzitjenu/`. 

Then, clone all repositories there, so you get the following directory structure:

```
waarzitjenu/
├── auth
├── database
├── documentation
├── map
└── server
```



- Cloning with the GitHub CLI (recommended)

  ```sh
  mkdir -p ~/GitHub/waarzitjenu/ && cd $_
  gh repo clone waarzitjenu/auth
  gh repo clone waarzitjenu/database
  gh repo clone waarzitjenu/documentation
  gh repo clone waarzitjenu/map
  gh repo clone waarzitjenu/server
  ```


- Git (SSH)

  ```sh
  mkdir -p ~/GitHub/waarzitjenu/ && cd $_
  git clone git@github.com:waarzitjenu/auth.git
  git clone git@github.com:waarzitjenu/database.git
  git clone git@github.com:waarzitjenu/documentation.git
  git clone git@github.com:waarzitjenu/map.git
  git clone git@github.com:waarzitjenu/server.git
  ```

- Git (HTTPS)

  ```sh
  mkdir -p ~/GitHub/waarzitjenu/ && cd $_
  git clone https://github.com/waarzitjenu/auth.git
  git clone https://github.com/waarzitjenu/database.git
  git clone https://github.com/waarzitjenu/documentation.git
  git clone https://github.com/waarzitjenu/map.git
  git clone https://github.com/waarzitjenu/server.git
  ```


## Step 2: Letting the waarzitjenu/server use the local packages

This step is important. If you are planning to work on one of the Go modules, you should let the server package know to use the local packages instead of the online ones. Open `go.mod` in `waarzitjenu/server`, and add the following to the end of the file:

```gomod
replace (
  github.com/waarzitjenu/auth v1.0.0 => ../auth
  github.com/waarzitjenu/database v1.1.0 => ../database
)
```

This will tell Go not to fetch the database from GitHub directly, but use the local package instead.

> Note: If Go is already using the online packages, issue the following commands to remove the packages and reset the checksums:
>
> ```sh
> sudo rm -rf $GOPATH/pkg/github.com/waarzitjenu
> rm server/go.sum
> ```
>
> Then, try to use the server middleware again.

## Step 3: Edit your modules

Now you can work on the modules, for example, add new functionality to the authentication module and adapt the server package so it uses it. :+1:

## Step 4: Submit a pull request

If you're done, be sure to commit all changes except the one made to `go.mod` and submit a pull request.

