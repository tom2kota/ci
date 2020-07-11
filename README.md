# CI - continuous integration
[Top 8 Continuous Integration Tools:](https://code-maze.com/top-8-continuous-integration-tools/)

- [Buddy](https://buddy.works/)

- [TeamCity](https://www.jetbrains.com/teamcity/)

- [Jenkins](https://www.jenkins.io/)

- [Travis CI](https://travis-ci.org/)

- [Bamboo](https://www.atlassian.com/software/bamboo)

- [GitLab CI](https://about.gitlab.com/)

- [CircleCI](https://circleci.com/)

- [Codeship](https://codeship.com/)


### Example of CI with CircleCI:


[Continuous Integration for robofriends app:](https://github.com/aneagoie/robofriends-ci)


```
# .circleci/config.yml

version: 2
jobs:
   build:
     docker:
       - image: circleci/node:8.9
     steps:
       - checkout
       - run: npm install
       - run: CI=true npm run build
   test:
     docker:
       - image: circleci/node:8.9
     steps:
       - checkout
       - run: npm install
       - run: npm run test
   hithere:
     docker:
       - image: circleci/node:8.9
     steps:
       - checkout
       - run: echo "Hellloooo!"
workflows:
  version: 2
  build-test-and-lint:
    jobs:
      - build
      - hithere
      - test:
          requires:
            - hithere

```
