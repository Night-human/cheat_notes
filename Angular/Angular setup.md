# Angular Installation

## Linux

> Install Node

- Download [node](https://nodejs.org) and decompress it at an easy access folder
- Rename the decompressed folder as **nodejs**
- Edit the **.profile** file and add the next code at the bottom

    If the parent folder were your home directory:
    ```
    #node
    export PATH=$HOME/nodejs/bin:$PATH
    ```
- Logout or exec in the console:
    ```
    . ~./profile
    ```
> Install Angular

- exec in the console:

    ```
    npm i -g @angular/cli
    ```