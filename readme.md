# Framgia CI for Laravel project

[![Build Status](http://ci.framgia.vn/api/badges/tuanpht/laravel57-framgiaci-test/status.svg)](http://ci.framgia.vn/tuanpht/laravel57-framgiaci-test)

- [Framgia-CI Document](https://github.com/framgia/ci-service-document)
- Steps
  + Add `.drone.yml`, `.framgia-ci.yml`, see [example](https://github.com/framgia/ci-service-document/tree/master/php), [document](https://github.com/framgia/ci-report-tool/)
  + Activate repository in http://ci.framgia.vn/
  + If Github repository is private:
    * Go to ci.framgia.vn repo `SETTINGS` -> Copy value of `Public Key`
    * Go to Github repository Setting -> Add Delpoy Key
  + If you want to use some secret value in `.drone.yml`:
    * Go to ci.framgia.vn repo `SECRETS` -> Define key, value as `YAML` format
      ```yml
      CHATWORK_ROOM_ID: abc
      CHATWORK_TOKEN: secret
      ```
    * Generate and copy encrypted key to file `.drone.sec`
    * Start using in `.drone.yml`:
      ```yml
      notify:
        chatwork:
        image: fdplugins/chatwork
        room_id: $$CHATWORK_ROOM_ID
        token: $$CHATWORK_TOKEN
        format: "TO ALL >>>..."
        when:
          event: push
      ```
- Tips:
  + Custom `phpcs` standard
    * Create file `phpcs.xml` in root project dir
    * Edit `phpcs` command in `.framgia-ci.yml` if needed
      ```diff
      -    command: phpcs --runtime-set ignore_warnings_on_exit 1 --standard=Framgia
      +    command: phpcs --runtime-set ignore_warnings_on_exit 1 --standard=phpcs.xml
      ```
