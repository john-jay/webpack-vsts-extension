# webpack build task

### A build task for [Visual Studio Team Services (VSTS)](https://www.visualstudio.com/fr-fr/products/visual-studio-team-services-vs.aspx) made with ♥ by

[![dealogic logo](https://raw.githubusercontent.com/Dealogic/webpack-vsts-extension/master/dealogic-logo.png)](http://www.dealogic.com)

### to bundle your assets, scripts, images and styles with webpack.

![build status](https://dealogic.visualstudio.com/DefaultCollection/_apis/public/build/definitions/4cd19643-db3a-4dcc-b481-76a7800dd64d/7871/badge)

## Content

* [Installation](https://marketplace.visualstudio.com/items?itemName=Dealogic.webpack-vsts-extension#installation)
* [Source Code](https://marketplace.visualstudio.com/items?itemName=Dealogic.webpack-vsts-extension#source-code)
* [What The Build Step Does](https://marketplace.visualstudio.com/items?itemName=Dealogic.webpack-vsts-extension#what-the-build-step-does)
* [Usage](https://marketplace.visualstudio.com/items?itemName=Dealogic.webpack-vsts-extension#usage)
    * [Advanced Settings](https://marketplace.visualstudio.com/items?itemName=Dealogic.webpack-vsts-extension#advanced-settings)
    * [Multiple Build Steps](https://marketplace.visualstudio.com/items?itemName=Dealogic.webpack-vsts-extension#multiple-build-steps)
* [Summary of Task Settings](https://marketplace.visualstudio.com/items?itemName=Dealogic.webpack-vsts-extension#summary-of-task-settings)
* [Release Notes](https://marketplace.visualstudio.com/items?itemName=Dealogic.webpack-vsts-extension#release-notes)
* [License](https://marketplace.visualstudio.com/items?itemName=Dealogic.webpack-vsts-extension#license)

## <a id="installation"></a>Installation

Installation can be done using [Visual Studio MarketPlace](https://marketplace.visualstudio.com/items?itemName=Dealogic.webpack-vsts-extension).

## <a id="source-code"></a>Source Code

Source code can be found on [GitHub](https://github.com/Dealogic/webpack-vsts-extension).

## <a id="what-the-build-step-does"></a>What The Build Step Does

This build step is using the webpack's node.js API to compile a 'web' application into a bundle. The result, warnings and errors are reported onto the build summary section.

## <a id="usage"></a>Usage

Add the task to your build configuration:

![Add webpack task](https://raw.githubusercontent.com/Dealogic/webpack-vsts-extension/master/screenshots/TaskCatalog.png)

By default without any configuration the build task is trying to run the locally installed webpack.js from the root folder in the repository and trying to pick up the `webpack.config.js`.

Through the `webpack config location` setting the webpack config can be modified:

```
./webpack.dist.config.js
```

Errors and Warnings can be treated differently:
* treat errors as (errors / warnings / info)
* treat warnings as (errors / warnings / info)

Warnings means the task will partially succeed, in case of errors the task will fail. If there are no errors and no warnings, then the task will succeed. You can treat the errors as warnings, so in case of errors, the task will just partially succeed. Or if you would like to ignore the warnings, those should be handled as info.

![webpack arguments](https://raw.githubusercontent.com/Dealogic/webpack-vsts-extension/master/screenshots/WebpackArguments.png)

The webpack build errors and warnings are reported under the issues / build section on the summary page:

![webpack build issues](https://raw.githubusercontent.com/Dealogic/webpack-vsts-extension/master/screenshots/WebpackBuildIssues.png)

The webpack build result section is added onto the summary page to summarize the result:

![webpack build result](https://raw.githubusercontent.com/Dealogic/webpack-vsts-extension/master/screenshots/WebpackBuildResult.png)

### <a id="advanced-settings"></a>Advanced Settings

- Working folder where webpack command is run. If you leave it blank it is the root of the repo.
- Location of the webpack module. If you leave it blank it is using the locally installed webpack node module in the working folder, e.g. `./node_modules/webpack`.

![Advanced settings](https://raw.githubusercontent.com/Dealogic/webpack-vsts-extension/master/screenshots/AdvancedSettings.png)

### <a id="multiple-build-steps"></a>Multiple Build Steps

Multiple webpack build steps are supported now. To distinguish the webpack build steps on the summary page
and in the list of issues, set the display name properly for the steps:

![Multiple setps with different name](https://raw.githubusercontent.com/Dealogic/webpack-vsts-extension/master/screenshots/MultipleStepsWithDifferentName.png)

If the webpack projects are not even in the root folder, then don't forget to modify it in the advanced settings like this:

![Different working folder](https://raw.githubusercontent.com/Dealogic/webpack-vsts-extension/master/screenshots/ModifiedWorkingFolder.png)

The issues in case of multiple build steps:

![Issues section for multiple steps](https://raw.githubusercontent.com/Dealogic/webpack-vsts-extension/master/screenshots/IssuesForMultipleSteps.png)

The result sections in case of multiple build steps:

![Result sections for multiple steps](https://raw.githubusercontent.com/Dealogic/webpack-vsts-extension/master/screenshots/ResultSectionsForMultipleSteps.png)

## <a id="summary-of-task-settings"></a>Summary of Task Settings

Name | Required | Default Value | Description
--- | :---: | --- | ---
webpack config location | true | ./webpack.config.js | The location of the configuration for the webpack compilation. Relative to the working folder.
treat errors as | true | errors | How to treat errors. Options are: errors (breaks build) / warnings (marks build as partially succeeded) / info (reports errors as info).
treat warnings as | true | warnings | How to treat warnings. Options are: errors (breaks build) / warnings (marks build partially succeeded) / info (reports warnings as info).
workingFolder | false | | Working folder where webpack compilation is run. If you leave it blank it is the root of the repository.
webpack module location | false | | Location of the webpack module. If you leave it blank it is the locally installed 'webpack' module.
ts-node module location | false | | Location of the ts-node module. If you leave it blank it is the locally installed 'ts-node' module.
ts-node options location | false | | Location of the ts-node options. If you leave it blank the ts-node default options will be used.

## <a id="release-notes"></a>Release Notes

* 3.1.0 (29/08/2017)
    * Support for TypeScript webpack configuration is added.
    * The ts-node module location can be modified.
    * The ts-node module options file location can be supplied.
* 3.0.19 (03/07/2017)
    * As the build step is using webpack's node.js API the arguments setting is gone. Instead of that there's the webpack config file location where custom configuration files can be specified for the compilation.
    * The setting of webpack.js location is gone, instead of that use webpack module location if you don't want to use the locally installed webpack module.
    * The webpack build step summary section is using webpack node.js API to show the result information.
    * The webpack build step now is logging the summary section onto the log section as well.

* 2.1.3 (22/05/2017)
* 2.1.2 (22/05/2017)
* 2.1.0 (22/05/2017)
* 2.0.2 (16/05/2017)
* 1.1.1 (29/03/2017)
* 1.1.0 (21/01/2017)

## <a id="license"></a>License

[MIT](https://github.com/Dealogic/webpack-vsts-extension/blob/master/LICENSE)