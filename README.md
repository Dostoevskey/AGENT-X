# ![AGENT-X Logo](documentation/agent-x-logo-blue.png) AGENT-X

AGENT-X is the label helper component for [AGENT](https://github.com/UltimateSoftware/AGENT), once installed in Chrome it allows for the labeling of HTML elements for training.

![A gif of AGENT-X in action](documentation/intro.gif)

## Installation

To install AGENT-X follow the steps below:

* Clone the project
* [Build](#build) the project
* Open Chrome
* Go to More Tools -> Extensions
* Flip the Develop toggle
* Click the button 'Load unpacked'
* Select the `dist/agent-x` folder in the project you cloned earlier.
* The AGENT-X icon should now be present in Chrome, click on it to ensure it installed properly.

## User Guide

For a description of the architecture and design of AGENT-X and the associated AGENT project, read the [AI Generation and Exploration in Test System (Agent) and Agent-X User's Guide](./documentation/user_guide.md).

## Development

The project is divided into two parts, the PopOver (The small window that appears when the Chrome extension icons is clicked) and the "extension" which handles communication between the PopOver and the web page, as well as interactions with the web page. The "extension" is composed of two major compontents, "Background" and "Content". Content communicates with both the PopOver and Background and is the only method for interacting with the page. Background handles background processes, like API calls. The PopOver project is an Angular 7 application located under `src/app` while the "extension" is a vanilla JavaScript project located in the `src/extension` folder.

The Chrome Message Passing framework facilitates communication between the components. It is recommended that you read [this](https://developer.chrome.com/extensions/messaging) page if you are unfamilar with Chrome Message Passing.

JQuery is used to interact with the DOM.

Finally, Angular 7 and RXJS Observables are used for the PopOver. All external interacations to the PopOver are wrapped in Observables in services. This allows for a clean sepeartion of concerns and to re-zone the callbacks since the Chrome APIs exit the NgZone. If you are unfamilar with RXJS Observables it is recommended that you read [this](https://www.learnrxjs.io/).

### Build

First, you need to install NodeJS on your machine. If you are on mac, this can easily be done using `nvm`.
See installation instructions for nvm here: https://github.com/creationix/nvm#installation-and-update

Once you have nvm installed, after cloning this project, you can execute the following commands:

`nvm install 10.15.1`

`nvm use 10.15.1`

Next, install `yarn` and the Angular CLI:

`npm install -g yarn`

`npm install -g @angular/cli`

Next, execute yarn on the root directory of this repo:

`yarn`

Finally, run `ng build --prod` to build the extension.

More details:
Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build. Since the popover loads each time the Chrome Extension icon is clicked, it is recommended to use `--prod` to mitigate delayed popup responses. This build command will also transpile and copy both the PopOver and "extension" dependencies.

Once the application has been built you can re-install it in a similar fashion to the Installation steps above:

* Go to More Tools -> Extensions
* Click the button 'Load unpacked'
* Select the dist/agent-x folder

### Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

### Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).

## Contributors

Adamo, David   
Alt, Patrick   
Briggs, Keith   
Celli, Nicolette   
Clarke, Peter J.   
Daye, Philip   
King, Tariq   
Phillips, Justin   
Santiago, Dionny   

## References
Santiago, D. (2018). A model-based AI-driven test generation system (Unpublished master's thesis). Miami, Florida, Florida International University. Retrieved February 5, 2019.

Santiago, D., Clarke, P. J., Alt, P., & King, T. M. (2018). Abstract flow learning for web application test generation. Proceedings of the 9th ACM SIGSOFT International Workshop on Automating TEST Case Design, Selection, and Evaluation - A-TEST 2018, 49-55. doi:10.1145/3278186.3278194

Santiago, D., King, T., & Clarke, P. (2018). AI-driven test generation: Machine learning from human testers. 37th Annual Pacific NW Software Quality Conference.
