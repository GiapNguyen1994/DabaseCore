# Module DataBase - ViettelPay App

This guide shows how to use Module DataBase in ViettelPay App

## Table of content
- [Setup database module](#setup-database-module)
- [Usage](#usage)

## Setup database module
- Add these lines at ```onCreate()``` in ```App.java```
```java
        KPreferences.init(this, R.string.app_name.getString(this))
        KeyStoreController.init(this)
 ```
- And add ```databaseModule and repositoryModule``` for initiating Koin
