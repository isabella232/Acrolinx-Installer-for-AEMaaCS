# Acrolinx-installer-for-AEMaaCS

## Steps for adding Acrolinx to AEM as a Cloud Service

Follow this step-by-step guide to integrate Acrolinx to your existing code repository.

## Adding Acrolinx module

- Create a clone of your Cloud Manager&#39;s Git repository.
- Copy the Acrolinx module from this repository to root directory of the cloud manager code.
- Update  **/acrolinx/pom.xml**

  - Replace the parent pom section with your parent&#39;s pom details, as shown below:

  - Update the artifact Id as per your application&#39;s naming convention:

- Update  **/acrolinx/acrolinx.installer/pom.xml**

  - Update the artifact id as per your application&#39;s naming conventions.

- Add the Acrolinx module in the parent pom module section.
