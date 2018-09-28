# Framgia CI for Laravel project

- [Framgia-CI Document](https://github.com/framgia/ci-service-document)
- Steps
  + Add `.drone.yml`, `.framgia-ci.yml`, see [example](https://github.com/framgia/ci-service-document/tree/master/php), [document](https://github.com/framgia/ci-report-tool/)
  + Activate repository in http://ci.framgia.vn/
  + If Github repository is private:
    * Go to ci.framgia.vn repo `SETTINGS` -> Copy value of `Public Key`
    * Go to Github repository Setting -> Add Delpoy Key
