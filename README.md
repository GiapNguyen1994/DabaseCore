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
        
```
- Using Keystore 
```java 
        KeyStoreController.KEY.encryptByKeyStore(value)
        KeyStoreController.KEY.decryptByKeyStore()
        KeyStoreController.KEY.removeKey()
```

- Using room database
  + Room database in DabaseCore using to store ```Listservice, Contact and UserInfo``` . Feature module only call funtions which are defined on DatabaseCore and don't have permision to edit 
Feature module should create database for each module
1. In Order to create Room database in feature module, add key to encrypt room
```java
        fun provideSupportFactory(): SupportFactory {
          val dbKey = RoomKeyMgr.getInstance().getCharKey(KEY)
          val passphrase = SQLiteDatabase.getBytes(dbKey)
          return SupportFactory(passphrase)
        }

KEY: key of each module to encrypt room
```
2. Get Contact
```java
        val contactFetcher: ContactFetcher by inject()
        contactFetcher.addCallback(contacts -> todo() );
        contactFetcher.fetch(this, false);
        contactFetcher.removeCallback(calBack);
```

3. Get, save, delete UserInfo
```java 
        val serInfoController: UserInfoController by inject()
        serInfoController.getUserInfo()
        serInfoController.saveUserInfo()
        serInfoController.deleteUserInfo()
```

4. Get, save, delete ListService
    + Using ListServiceRepository with: 

```java 
       suspend fun insertAllService(allService: AllService)
       fun getAllService(): List<AllService>
       suspend fun insertServicePayment(servicePayment: ServicePayment)
       fun getServicePayment(): List<ServicePayment>
```


