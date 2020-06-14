# For developers

We also have a Maven repository for Java developers who want to create add-ons for our plugin\(s\).

### The repository:

{% code title="pom.xml" %}
```markup
<repository>
    <id>iobyte-repo</id>
    <url>https://nexus.iobyte.nl/repository/maven-public/</url>
</repository>
```
{% endcode %}

### ThemePark:

{% code title="pom.xml" %}
```markup
<dependency>
    <groupId>me.paradoxpixel</groupId>
    <artifactId>themepark.api</artifactId>
    <version>1.0</version>
    <scope>provided</scope>
</dependency>
```
{% endcode %}

The Javadocs are available at [https://sbdplugins.nl/javadoc/themepark](http://sbdplugins.nl/javadoc/themepark)

### ThemeParkPlus:

{% code title="pom.xml" %}
```markup
<dependency>
    <groupId>nl.sbdevelopment</groupId>
    <artifactId>themeparkplus.api</artifactId>
    <version>1.0</version>
    <scope>provided</scope>
</dependency>
```
{% endcode %}

The Javadocs are available at [https://sbdplugins.nl/javadoc/themeparkplus/](https://sbdplugins.nl/javadoc/themeparkplus/)

