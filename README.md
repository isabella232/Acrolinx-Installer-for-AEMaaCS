# Acrolinx-Installer-for-AEMaaCS

## Steps for adding Acrolinx to AEM as a Cloud Service

Follow this step-by-step guide to integrate Acrolinx to your existing code repository.

## Adding Acrolinx module

- Create a clone of your Cloud Manager's Git repository.
- Copy the Acrolinx module from this repository to root directory of the cloud manager code.
- Update  **/acrolinx/pom.xml**

  - Replace the parent pom section with your parent&#39;s pom details, as shown below:

  ```xml
  <!-- Replace with your parent project details-->
  <parent>
        <groupId>com.adobe.aem.guides</groupId> 
        <artifactId>aem-guides-wknd</artifactId> 
        <version>1.1.1-SNAPSHOT</version>
        <relativePath>../pom.xml</relativePath>
  </parent>
  ```

  - Update the artifact Id as per your application's naming convention:

  ```xml
  <artifactId>aemaacs-acrolinx-project-acrolinx-manager</artifactId>
  ```

- Update  **/acrolinx/acrolinx.installer/pom.xml**

  - Update the artifact id as per your application's naming conventions.

  ```xml
  <artifactId>aemaacs-acrolinx-project-acrolinx-installer</artifactId>
  ```

- Add the Acrolinx module in the parent pom module section.

  ```xml
  <modules>
        <module>all</module>
        <module>core</module>
        <module>ui.frontend</module>
        <module>ui.apps</module>
        <module>ui.apps.structure</module>
        <module>ui.config</module>
        <module>ui.content</module>
        <module>ui.content.sample</module>
        <module>it.tests</module>
        <module>dispatcher</module>
        <module>ui.tests</module>
        <module>acrolinx</module> <!-- Add acrolinx module -->
    </modules>
  ```

- Add a dependency to `all` module for acrolinx installer

  In `all` module's pom.xml add:

  ```xml
  <dependency>
    <groupId>com.acrolinx.client</groupId>
    <artifactId>aemaacs-acrolinx-project-acrolinx-installer</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <type>zip</type>
  </dependency>
  ```

  In plugin section of the `all` module under the `filevault-package-maven-plugin` add a `embedded` section similar to other other modules.

  ```xml
  <embeddeds>
    <embedded>
      <groupId>com.acrolinx.client</groupId>
      <artifactId>aemaacs-acrolinx-project-acrolinx-installer</artifactId>
      <type>zip</type>
      <target>/apps/wknd-packages/application/install</target>
    </embedded>
  </embeddeds>
  ```
