# MKCERT !! Windows 11 !! { Symfony 6 }

If you are using Symfony's built-in build system or if you are using Docker, this tutorial is not for you.
destined. However, if you are in my case and you use a local server on your machine, like Wampserver,
then this tutorial will be useful for you.

Question: why opt for a local server on your machine? The answer is simple: when you develop
Android applications that connect to a Symfony API, there may be constraints related to HTTPS. In this
context, you might not really have a choice (easier to solve)


[![2023-08-21-23-36-25.png](https://i.postimg.cc/k5rhxCCR/2023-08-21-23-36-25.png)](https://postimg.cc/JsqqL9GR)
[![2023-08-21-23-34-20.png](https://i.postimg.cc/KvGbMnfh/2023-08-21-23-34-20.png)](https://postimg.cc/fkr14S18)
[![2023-08-21-23-38-09.png](https://i.postimg.cc/Vs7GKn18/2023-08-21-23-38-09.png)](https://postimg.cc/rzrNmdKn)

## Environment !!
* Windows 11 64 bits 
* WampServer 3.3.1
* Apache 2.4.55
* PHP 8.1.21
* MariaDB 10.6.5
* Node.js 18.17.1
* NPM 9.8.1.

## Installation
1. chocolatey
2. Scoop
3. Symfony CLI
4. MkCert
5. MakeFile

Install chocolatey  -> Select Windows Powershell(Admin)

[chocolatey.org](https://community.chocolatey.org/courses/installation/installing?method=installing-chocolatey)

````
    Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
`````
Install Scoop  -> Select Windows Powershell(Admin)

[Scoop.sh](https://scoop.sh/)

````
    > Set-ExecutionPolicy RemoteSigned -Scope CurrentUser # Optional: Needed to run a remote script the first time
    > irm get.scoop.sh | iex
`````
Assume you haven't installed symfony CLI yet

[symfony.com](https://symfony.com/download)

````
    $ scoop install symfony-cli
`````

[MKCERT by chocolatey ](https://github.com/FiloSottile/mkcert#windows)

````
    > choco install mkcert
`````

[MakeFile by chocolatey](https://community.chocolatey.org/packages/make)

````
    > choco install make
`````

**WWOOOOO:** 
..... Done 🎈

**THEN :**

[MKCERT command ](https://github.com/FiloSottile/mkcert#mkcert)

````
    $ mkcert -install
`````
````
    Created a new local CA 💥
    The local CA is now installed in the system trust store! ⚡️
    The local CA is now installed in the Firefox trust store (requires browser restart)! 🦊
`````

````
    $ mkcert example.com "*.example.com" example.test localhost 127.0.0.1 ::1
`````
````
    Created a new certificate valid for the following names 📜
        - "example.com"
        - "*.example.com"
        - "example.test"
        - "localhost"
        - "127.0.0.1"
        - "::1"

    The certificate is at "./example.com+5.pem" and the key at "./example.com+5-key.pem" ✅
`````
Advance ->
````
    mkcert -key-file /path/to/key.pem -cert-file /path/to/cert.pem example.com *.example.com
`````

````
    > make set-ssl  nameDomain="domaine.wip" 
    
    #---MKCERT-#
    MKCERT = mkcert
    MKCERT_INSTALL = $(MKCERT) -install
    #------------#
    
    ...........................

    CompileAndRun: CompileFile RunFile
    
    CompileFile:
        (Compiling code)
    
    set-ssl:
        IF exist "./config/ssl" ( echo "./config/ssl" exists ) ELSE ( mkdir "./config/ssl" && echo "./config/ssl" created)
        $(MKCERT) -key-file ./config/ssl/_wildcard.$(nameDomain)-key.pem -cert-file ./config/ssl/_wildcard.$(nameDomain).pem *.$(nameDomain)
`````

## Contributing

If you want to contribute \(thank you!\) to this bundle, here are some guidelines:

* Please respect the [Symfony guidelines](http://symfony.com/doc/current/contributing/code/standards.html)
* Test everything! Please add tests cases to the tests/ directory when:
    * You fix a bug that wasn't covered before
    * You add a new feature
    * You see code that works but isn't covered by any tests \(there is a special place in heaven for you\)

## Todo

* Packagist

## Thanks
