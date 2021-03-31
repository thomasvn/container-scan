# JFrog Xray (free trial)


## Pushing your image to artifactory (container registry) and running the scan
1. Set up repository (on Admin panel)
    - package type = Docker
2. Add repo as an "indexed resource" (on Admin panel)
    - XRay Security & Compliance -> General -> Indexed Resources
3. Retag your image and push to JFrog Platform
    - `docker image tag ubi7:7.9 thomasvn.jfrog.io/ubi-7/ubi7:7.9`
    - `docker push thomasvn.jfrog.io/ubi-7/ubi7:7.9`
4. Set up a new "scan policy" (on Application panel)
    - Security & Compliance -> Policies
    - Default will generate report violations of all severities
5. Set up a "watch" (on Application panel)
    - Security & Compliance -> Watches
    - declare which policies to apply to which resources
6. Generate a "report"


## Removing vulnerable libraries (RedHat)



## References
- https://www.youtube.com/watch?v=bf3iKXMpr68
- https://www.jfrog.com/confluence/display/JFROG/Xray+Reports#XrayReports-ViolationsReport