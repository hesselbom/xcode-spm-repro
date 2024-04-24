Project to demonstrate issue described in https://github.com/EvanBacon/xcode/issues/6

Created using:
```bash
npx create-expo-app@latest xcode-spm-repro
npm i @bacons/apple-targets
// Added apple watch target code
npx expo prebuild
// Added Swift Package "Supabase" to Apple Watch project
npx expo prebuild
// Error
```

### Reproduce error
Run `npm i` to install all dependencies then `npx expo prebuild` and you'll get the following error:
```bash
✔ Created native directories | reusing /android, /ios
✔ Updated package.json | no changes
You're using an experimental Config Plugin that is subject to breaking changes and has no E2E tests.
[Malformed Xcode project]: Found orphaned reference: AC9C55BE2BD9246500041977 > PBXBuildFile.productRef > AC9C55BD2BD9246500041977
[Malformed Xcode project]: Found orphaned reference: DCA0157385AE428CB5B4F71F > PBXNativeTarget.packageProductDependencies > AC9C55BD2BD9246500041977
[Malformed Xcode project]: Found orphaned reference: 83CBB9F71A601CBA00E9B192 > PBXProject.packageReferences > AC9C55BC2BD9246500041977
Target "watchApp" already exists, updating instead of creating a new one
✖ Prebuild failed
Error: [ios.xcodeProjectBeta2]: withIosXcodeProjectBeta2BaseMod: Unable to serialize object: 'AC9C55BD2BD9246500041977'
Error: [ios.xcodeProjectBeta2]: withIosXcodeProjectBeta2BaseMod: Unable to serialize object: 'AC9C55BD2BD9246500041977'
    at PBXBuildFile.toJSON (~/xcode-spm-repro/node_modules/@bacons/xcode/build/api/AbstractObject.js:118:27)
    at XcodeProject.toJSON (~/xcode-spm-repro/node_modules/@bacons/xcode/build/api/XcodeProject.js:194:38)
    at write (~/xcode-spm-repro/node_modules/@bacons/apple-targets/build/withXcparse.js:68:66)
    at action (~/xcode-spm-repro/node_modules/@expo/config-plugins/build/plugins/createBaseMod.js:67:17)
    at async interceptingMod (~/xcode-spm-repro/node_modules/@expo/config-plugins/build/plugins/withMod.js:105:21)
    at async evalModsAsync (~/xcode-spm-repro/node_modules/@expo/config-plugins/build/plugins/mod-compiler.js:210:25)
    at async Object.compileModsAsync (~/xcode-spm-repro/node_modules/@expo/config-plugins/build/plugins/mod-compiler.js:125:10)
    at async configureProjectAsync (~/xcode-spm-repro/node_modules/@expo/cli/build/src/prebuild/configureProjectAsync.js:56:14)
    at async prebuildAsync (~/xcode-spm-repro/node_modules/@expo/cli/build/src/prebuild/prebuildAsync.js:117:9)
```
