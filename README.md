## jacoco-agent-docker

Simple image to provide an up-to-date jacoco Java agent as a volume container

### Usage
```
version: '3.8'
services:
    jacoco:
        image: harleybaker/jacoco-agent-docker:0.8.8
        volumes:
            - jacoco:/jacoco:ro
    www:
        environment:
            JAVA_TOOL_OPTIONS: -javaagent:/jacoco/lib/jacocoagent.jar=excludes=*_javassit_*:javax.xml.soap.*:oasis.*,output=tcpserver,address=*
    image: httpd
    volumes:
        - jacoco:/jacoco:ro
volumes:
    jacoco:
```