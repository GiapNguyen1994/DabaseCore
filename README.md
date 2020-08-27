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

## Usage
- There are two SharePreferences type" NonEncryption and Encryption
1. Using SharePreferences Encryption
```java
        KPreferences.KEY.putString(value)
        KPreferences.KEY.getString(defaultValue)
        KPreferences.KEY.putInt(value)
        KPreferences.KEY.getInt(defaultValue)
        KPreferences.KEY.putLong(defaultValue)
        KPreferences.KEY.getLong(defaultValue)
        KPreferences.KEY.putBoolean(defaultValue)
        KPreferences.KEY.getBoolean(defaultValue)
        
```
2. Using SharePreferences NonEncryption
```java
        KPreferences.KEY.putStringNotEncrypt(value)
        KPreferences.KEY.getStringNotEncrypt(defaultValue)
        KPreferences.KEY.putIntNotEncrypt(value)
        KPreferences.KEY.getIntNotEncrypt(defaultValue)
        KPreferences.KEY.putLongNotEncrypt(defaultValue)
        KPreferences.KEY.getLongNotEncrypt(defaultValue)
        KPreferences.KEY.putBooleanNotEncrypt(defaultValue)
        KPreferences.KEY.getBooleanNotEncrypt(defaultValue)
