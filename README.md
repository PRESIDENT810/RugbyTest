# Instruction to reproduce

Before doing the following, make sure this repo is fresh cloned or cleaned by `git clean -ffdx`. Also, use `rugby clear` to clear global rugby cache (not sure if this step is necessary but better to be safe and keep our environment clean).

Install React Native things and prepare the Xcode project:
```
yarn install
bundle install
bundle exec pod install --project-directory=ios --repo-update
```

Note: at this moment, you can see `ios/build/generated/ios/FBReactNativeSpec/FBReactNativeSpec-generated.mm` and `ios/build/generated/ios/FBReactNativeSpec/FBReactNativeSpec.h` are empty.

If we don't use rugby, everything is normal. Just open Xcode and build it.

If use rugby:

```
cd ios
rugby cache --arch arm64 --config Debug --sdk ios
```

After this step, you can see the generated content in `ios/build/generated/ios/FBReactNativeSpec/FBReactNativeSpec-generated.mm` and `ios/build/generated/ios/FBReactNativeSpec/FBReactNativeSpec.h`, which are no longer empty.

Now if you open Xcode and build, it's going to fail due to a bunch of libraries not found.

However, if you do pod install and rugby again, Xcode will somehow successfully build it. I'm not sure if the application works normally or not...
