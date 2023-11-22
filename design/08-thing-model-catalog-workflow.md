# Thing Model Catalog
## Worflow Description

This design document proposes a user experience for the catalog interface derived from the design goals described in issue [#8].

### Consumption

**Simple Search:**

A user want to use the official Thing Model catalog and downloads the ```tm-catalog-cli``` to interact with it. running it without paramters yields:

```
Usage:
  tm-catalog-cli [command]
  
Available Commands:
  add-repo
  login
  list
  search
  pull
  push
  create-toc
  validate

Flags:
  -h, --help   help for tm-catalog-cli
```

The user wants to find a Thing Model for the Siemens PowerCenter 1000 data transceiver and tries the following:

```
> ./tm-catalog-cli list powercenter

NAME                                 DESCRIPTION                                         STARS    QUALITY
enrico/pc1000-7KN1110.tm.jsonld      Well tested TM for Siemens PC1000 transceiver       40       Syn/Sem/Run/Man
siemens/7KN1110-0MC00.tm.jsonld      PowerCenter1000 transceiver official Thing Model    10       Syn/Sem/Run/-
thomas/powercenter1000.tm.jsonld     TM for the Siemens PowerCenter1000                  3        Syn/-/-/-
```

The user now wants to pick the TM with the most stars and use it:

```
> ./tm-catalog-cli fetch enrico/pc1000-7KN1110.jsonld
** Fetching enrico/pc1000-7KN1110.jsonld successful
```

and finds the file in the local directory. The user wants to find a TM for the arc fault detection device (AFDD) connected to the power center communication module, but the official catalog does not have a version available:

```
> ./tm-catalog-cli list afdd

NAME                                 DESCRIPTION                                         STARS    QUALITY

```

The user now searches the catalog of his/her organization, but needs to login beforehand:

```
> ./tm-catalog-cli add-repo thing-catalog.siemens.com
** Login to thing-catalog.siemens.com successful
```

Running the search again yields a hit:

```
> ./tm-catalog-cli list afdd

NAME                                 DESCRIPTION                                         STARS    QUALITY
siemens/wot_AFDDEM.jsonld            Official Thing Model for the AFDD module            20       Syn/Sem/Run/-
```

The user downloads it and starts using the Thing Model with their own WoT consumer

```
> ./tm-catalog-cli fetch siemens/wot_AFDDEM.jsonld
** Fetching siemens/wot_AFDDEM.jsonld successful
```

**Custom Catalog:**

The user has written some Thing Models for the current project, but they are not yet ready to be pushed to the companies or public catalogs. He/she wants to host them in a project-specific catalog. He creates a directory locally and imports his/her TMs:

```
> mkdir mycatalog; cd mycatalog
> tm-catalog-cli import ../thingmodels/*jsonld
** JSON Schema validation passed
** JSONLD Syntactic validation passed
** 1 Thing Model imported succesfully
** Table of Content created

> find .
doe/Siemens/3NACOM_FUSE/smartfuse.jsonld
catalog.toc.json
```

To test the catalog locally, the user runs an http-server on the directory:
```
> live-server .
Live server running on localhost port 8080
```

Searching with the cli works:
```
> tm-catalog-cli list --catalog-url=http://localhost:8080 "smart fuse"
NAME                                       DESCRIPTION                                         STARS    QUALITY
Siemens/3NACOM_FUSE/smartfuse.jsonld       WIP Thing Model for Siemens smart fuse              0        Syn/Sem/-/-
```

Now the user creates a git repository, adds all the files and pushes it to his/her github account at https://www.github.com/doe
```
> git init .
> git add .
> git commit -m "inital commit of TMs for project valhalla"
> git push --set-upstream git@github.com:doe/mycatalog
```

The user then adds this new repository to the list of registered repositories with the following command:
```
> tm-catalog-cli add-repo www.github.com:doe/mycatalog
** Registered catalog at https://raw.githubusercontent.com/doe/mycatalog
** Catalog contains 1 Thing Model
```

Running the search again without specifying the catalog URL works:
```
> tm-catalog-cli list "smart fuse"
NAME                                       DESCRIPTION                                         STARS    QUALITY
Siemens/3NACOM_FUSE/smartfuse.jsonld       WIP Thing Model for Siemens smart fuse              0        Syn/Sem/-/-
```






[#8]: https://github.com/web-of-things-open-source/proposal/issues/8
