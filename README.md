# Deploy From Repository

This role was created to automate the deployment of  applications that reside in artifact/code repositories.

## Dependences
None.

## Variables
```yml
    #Common Config - Should be always overwritten by your playbook
    app_name: The name of yout application.
    app_version: Version to be downloaded from repo
    app_dist_extension: Which extension the app is being released. Defualt: jar
    app_respository: Which repo technology We are working with.

    # Available Options - app_respository:
    # - artifactory (for JFrog Artifactory) ** Default Option
    # - local (for a network repo / mounted folder)

    # Artifactoy only variables
    artifactory_url: JFrog Artifactory URL
    artifactory_apikey: API Key, releated to a user with privileges to downloaded the artifact

    # Local only Variables
    local_path_mount: Local or Network root directory/folder
    local_package_path: Path to the artifact

    #Handling Artifact package
    app_unpack_package: Use true to unpack the artifact. Default: false
    app_package_dest: Where the artifact will be deployed. Default /opt/app_name
    app_package_replace: Force a replacement, in case this artifact was deployed previously. Default: true
```

## Example Playbook
```yml
    - hosts: application-server
      become: true
      roles:
         - role: deploy_from_repo
           vars:
              app_name: my_java_app
              app_version: 1.2.0
              app_dist_extension: war
              app_owner: jboss
              app_group: jboss
              app_respository: artifactory
              app_package_dest: /opt/wildfly/standalone/deployments
              artifactory_url: http://myartifactory.local.test/artifactory/releases/com/mock/my_java_app
              artifactory_apikey: p9w4erinv80W#HFINRige8beng$NI
```

## Compatibility

* [Ansible 2.+](https://www.ansible.com/)
* [CentOS 6 / 7](https://www.centos.org/)
* [JFrog Artifactory 4.x](https://jfrog.com/artifactory/)

## Contributing
Please read [CONTRIBUTING.md]([CONTRIBUTING.md]) for details on our code of conduct, and the process for submitting pull requests to me.

## Versioning
We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository]().

## Authors
*  [ArturFigueira](https://github.com/arturfigueira) - *Initial work*

## License
This project is licensed under the GNU GENERAL PUBLIC LICENSE - see the [LICENSE.md](LICENSE.md) file for details.
