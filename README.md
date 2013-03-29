# maven-karma-plugin
> **IMPORTANT**: This plugin still has to make it into Maven Central - watch this space!

> Note that this plugin began life as the [testacular-maven-plugin](https://github.com/kelveden/testacular-maven-plugin). Since Testacular itself has changed name to Karma, all subsequent development
of the plugin will be in its new form.

Provides the ability to run tests via [Karma](http://karma-runner.github.com/) as part of your Maven build.

## Usage

Note that the plugin expects Karma (and nodejs of course) to have been installed beforehand and for the `karma`
executable to be on the system path.

Example of a typical usage:

    <plugin>
        <groupId>com.kelveden</groupId>
        <artifactId>maven-karma-plugin</artifactId>
        <version>1.0</version>
        <executions>
            <execution>
                <goals>
                    <goal>start</goal>
                </goals>
            </execution>
        </executions>
        <configuration>
            <browsers>PhantomJS</browsers>
        </configuration>
    </plugin>

## More information

Just run:

    mvn help:describe -Dplugin=com.kelveden.plugins:maven-karma-plugin -Ddetail

The plugin simply shells out to `karma`; so the properties you specify in the configuration section will
be passed on as arguments to Karma itself. See the Karma
[configuration documentation](http://karma-runner.github.com/0.8/config/configuration-file.html) for more
information on the arguments available.

Note that only the subset of `karma start` arguments that are relevant are supported by the plugin - there's no
support for the `--port` argument, for example.

Note also that if a property isn't specified in the POM it will not be passed to `karma start` at all - i.e. Karma will
pick the default value for the corresponding argument. The exception to this rule is the "singleRun" property which is
set to "true" by default as this will be the most common use case in the context of a Maven build.

## Contributing

Bug reports are welcome - pull requests to fix aforementioned bugs even more so! Apart from that,
there really isn't much to the plugin and I think it's best to keep it that way. Am open to other thoughts on that though.
