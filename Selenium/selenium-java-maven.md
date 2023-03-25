# Selenium

## How to install

1. Install [JDK](https://www.oracle.com/mx/java/technologies/downloads/)
    - Add jdk to the system env variables

2. Install [maven](https://maven.apache.org/download.cgi)
    - Add maven to the system env variables

## Create a project

Use IDE or a plugin to do that, then add the selenium dependency and junit dependencie in the pom

## Run a test

From WebDriver instantiate a driver for the target web browser


        WebDriver driver = new FirefoxDriver();

        driver.get("https://www.google.com");
        System.out.println("Web page");
        System.out.println(driver.getCurrentUrl());
        System.out.println("web source");
        System.out.println(driver.getPageSource());
        Thread.sleep(10000);
        driver.close();

## Commands

- driver.get(url)   
Search for that url

- driver.finby