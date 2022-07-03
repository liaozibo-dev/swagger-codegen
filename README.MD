Swagger codegen maven 插件配置：
```xml
<build>
    <plugins>
        <plugin>
            <groupId>io.swagger</groupId>
            <artifactId>swagger-codegen-maven-plugin</artifactId>
            <version>2.3.1</version>
            <executions>
                <execution>
                    <goals>
                        <goal>generate</goal>
                    </goals>
                </execution>
            </executions>
            <configuration>
                <inputSpec>${project.basedir}/src/main/resources/api.yaml</inputSpec>
                <language>java</language>
                <output>${project.basedir}</output>
                <addCompileSourceRoot>true</addCompileSourceRoot>
                <modelPackage>com.liaozibo.study.swagger.model</modelPackage>
                <apiPackage>com.liaozibo.study.swagger.api</apiPackage>
                <invokerPackage>com.liaozibo.study.swagger.client</invokerPackage>
                <configOptions>
                    <sourceFolder>src/main/java</sourceFolder>
                </configOptions>
                <generateModelDocumentation>false</generateModelDocumentation>
                <generateApiDocumentation>false</generateApiDocumentation>
                <generateSupportingFiles>false</generateSupportingFiles>
            </configuration>
        </plugin>
    </plugins>
</build>
```

执行命令生成代码：
```
mvn clean compile
```

配置：
* `inputSpec`：OpenAPI 文档路径
* `language`：目标生成语言（java/spring）
* `output`：输出路径，默认是：`${project.build.directory}/generated-sources/swagger`
* `templateDirectory`：mustache 模板目录（mustache 是一个模板引擎）
* `addCompileSourceRoot`：将输出路径设置为 source root，默认是 `true`
* `modelPackage`：对象模型包路径
* `apiPackage`：API 接口包路径
* `invokerPackage`：调用代码包路径
* `modelNamePrefix`, `modelNameSuffix`：对象模型的前缀和后缀
* `withXml`：在生成的对象模型和 API 接口启用 XML 注解（仅支持 Java 语言）
* `configOptions`
* `configHelp`
* `ignoreFileOverride`：`.swagger-codegen-ignore` 的路径
* `generateApis`：生成 API 接口，默认是 `true`
* `generateApiTests`：生成 API 接口测试代码，默认是 `true`，只有 `generateApis` 是 true 时才有效
* `generateApiDocumentation`：生成 API 接口文档（Markdown 格式，在 doc 目录下），默认是 `true`，只有 `generateApis` 是 true 时才有效
* `generateModels`：生成对象模型
* `modelsToGenerate`：指定要生成的对象模型列表，以逗号分隔，默认是全部
* `generateModelTests`：生成对象模型测试代码，默认是 `true`，只有 `generateModels` 是 true 时才有效
* `generateModelDocumentation `：生成对象模型文档，默认是 `true`，只有 `generateModels` 是 true 时才有效
* `generateSupportingFiles`：生成支持文件，默认是 `true`，除了对象模型和接口代码文件，其他都是支持文件
* `supportingFilesToGenerate`：指定要生成的支持文件列表，以逗号分隔，默认是全部
* `skip`：跳过代码生成，默认是 `false`，也可以通过 `codegen.skip` 属性设置

[swagger-codegen](https://github.com/swagger-api/swagger-codegen/blob/master/modules/swagger-codegen-maven-plugin/README.md)