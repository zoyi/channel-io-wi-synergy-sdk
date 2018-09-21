# channel-io-wi-synergy-sdk

## Add dependency to `package.json`

```javascript
"dependencies": {
    "channel-io-wi-synergy-sdk": "git+https://github.com/zoyi/channel-io-wi-synergy-sdk.git",
}
```

## `npm install`

## `react-native link`

## Add dependency to `android/settings.gradle`

```gradle
include ':channel-io-wi-synergy-sdk'
project(':channel-io-wi-synergy-sdk').projectDir = new File(settingsDir, '../node_modules/channel-io-wi-synergy-sdk/android')
```

## Add dependency to `android/app/build.gradle`

```gradle
dependencies {
    compile project(':channel-io-wi-synergy-sdk')
}
```

## Add package to Application class

```java

import com.zoyi.channel.wi.android.ChannelPackage;

public class MyApplication extends MultiDexApplication implements ReactApplication {

  @Override
  protected List<ReactPackage> getPackages() {
    return Arrays.<ReactPackage>asList(
        new MainReactPackage(),
        new ChannelPackage()  // Here
    );
  }
}
```

## Call `ChannelIO.track` function in js code

We do not recommend calling this function often.

We recommend call `track` function when login succeed or application is start up

```javascript
import ChannelIO from 'channel-io-wi-synergy-sdk'

ChannelIO.track(
  pluginKey,
  userId,
  {
    age: 19,
    gender: 'male'
  }
).then(() => {
  console.log('success')
}).catch((error) => {
  console.log(error)
})
```

```javascript
ChannelIO.track(pluginKey, userId, profile)
```

* `pluginKey` (string, required)

  Channel plugin key


* `userId` (string, required)

  User id for specify user. It can be login id, hashed device id, etc...


* `profile` (object map, required)

  Profile information to logging. Map value can be `string`, `number`, `boolean`
