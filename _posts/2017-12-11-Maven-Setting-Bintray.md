---
layout: post
title: (Maven) Setting up bintray
---

```
<settings>
    <servers>
        <server>
          <id>bintray</id>
          <username>GITHUB-USER</username>
          <password>GITHUB-TOKEN</password>
        </server>
    </servers>
    <profiles>
        <profile>
            <repositories>
                <repository>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <id>central</id>
                    <name>bintray</name>
                    <url>http://jcenter.bintray.com</url>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <id>central</id>
                    <name>bintray-plugins</name>
                    <url>http://jcenter.bintray.com</url>
                </pluginRepository>
            </pluginRepositories>
            <id>bintray</id>
        </profile>
     </profiles>
    <activeProfiles>
        <activeProfile>bintray</activeProfile>
    </activeProfiles>
</settings>

```

