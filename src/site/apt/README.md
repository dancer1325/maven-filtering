* Origin
  * [maven-resources-plugin](https://maven.apache.org/plugins/maven-resources-plugin/index.html)'s filtering process
* allows
  * filtering resources

## MavenResourcesExecution
* POM Interpolation
  * expressions / are interpolated by POM values
    * `pom*`
    * `project*`
* Escaping Interpolation
  * `\${...}` -- would be interpolated to -- `${...}`
    * _Example:_ `\${java.home}` -> `${java.home}`
* `targetPath`
  * := parameter / accepts 
    * also absolute paths
* `overwrite`
  * := parameter /  
    * although destination file is newer -- forces -- file copy
## MavenResourcesFiltering
* allows
  * applying filtering to `List<org.apache.maven.model.Resource>`
    * predefined file extensions NOT filtered
      * 'jpg'
      * 'jpeg'
      * 'gif'
      * 'bmp'
      * 'png'
* if you want to use the default `List<FileUtils.FilterWrapper>` -- use it -> without `filterWrappers`
## MavenFileFilter
* := component /
  * has a method / returns the default `List<FileUtils.FilterWrapper>`, which are (interpolation + values):
    * `${ }` + values from
      * properties files 
        * `<project>/<build>/<filters, project.properties` OR
        * `<project>/<build>/<filters,mavenSession.executionProperties` OR
      * `mavenProject` interpolation
    * `@ @` + values from
      * properties files
        * `<project>/<build>/<filters, project.properties` OR
        * `<project>/<build>/<filters,mavenSession.executionProperties` OR
      * `mavenProject` interpolation
* values / used for interpolation
  * stored in `Properties` object
  * loaded in the next order
    * `List<PropertyFiles>` / -- provided as -- method's parameter
    * `<build>/<filters>` defined in the 'pom.xml'
    * `<properties>` defined in the 'pom.xml'
    * `executionProperties` from the current `MavenSession`

## Notes
* `Properties` object
  * last key/value overrides the previous ones

## Examples
* TODO: