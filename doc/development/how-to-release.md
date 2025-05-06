# How to release

An OpenAlea official release is scheduled on the 4th trimester of 2025.

All packages included in the [OpenAlea github organization](https://github.com/openalea) will be released.

To get the most homogeneous release, all package developers are invited to create an issue 
called **Release 2025 pckg-name**, with **pckg-name** being the name of the package to be released.
To do so and to ease the process, to create the issue please follow the next steps: 

- read the [guidelines](https://openalea.readthedocs.io/en/latest/development/guidelines.html) 
for developers.
- in the repository of the package **pckg-name** create a branch called *release* or *release 2025*. 
- create a new issue using the template *Release 2025*, call this issue **Release 2025 pckg-name**.
- associate this issue to the project **OpenAlea Release**.
- In the project set the status of the issue: *ready* or *in progress*,
to be *in progress*, the issue must be assigned.
- add a label to this issue, at least the label  *release2025*.
- it is possible to do sub-issues and pull request, to use different labels e.g. *refactoring*,
*test*, *documentation*, etc.
- for each pull request review should be asked.

When **pckg-name** is following all minimum requests the issue can be marked *done* with a final 
pull request accepted. The package **pckg-name** is ready for the release.

The requests for the release are:\
\- [ ] read the [guidelines](https://openalea.readthedocs.io/en/latest/development/guidelines.html)\
\- [ ] minimal README with (description, authors, installation instruction)\
\- [ ] License file\
\- [ ] pyproject.toml\
\- [ ] meta.yaml\
\- [ ] CI (.github/workflows/conda-package-build.yml)\
\- [ ] tests\
\- [ ] documentation\
\- [ ] tutorials\
\- [ ] Data management (share_data)
