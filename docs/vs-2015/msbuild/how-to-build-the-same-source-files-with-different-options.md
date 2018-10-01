---
title: 'Vorgehensweise: Erstellen identischer Quelldateien mit unterschiedlichen Optionen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55133fcd8126a5f77a670742b84ff83d9662520c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511091"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Gewusst wie: Erstellen identischer Quelldateien mit unterschiedlichen Optionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Erstellen identischer Quelldateien mit unterschiedlichen Optionen](https://docs.microsoft.com/visualstudio/msbuild/how-to-build-the-same-source-files-with-different-options).  
  
  
Wenn Sie Projekte erstellen, kompilieren Sie häufig die gleichen Komponenten mit unterschiedlichen Buildoptionen. So können Sie, z.B. ein Debugbuild mit Symbolinformationen oder ein Releasebuild ohne Symbolversionen, aber mit aktivierten Optimierungen erstellen. Oder Sie können ein Projekt erstellen, das auf einer bestimmten Plattform wie x86 oder [!INCLUDE[vcprx64](../includes/vcprx64-md.md)] ausgeführt wird. In allen diesen Fällen bleiben die meisten Buildoptionen gleich. Nur ein paar Optionen werden zur Steuerung der Buildkonfiguration geändert. Sie verwenden Eigenschaften und Bedingungen mit [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], um die unterschiedlichen Buildkonfigurationen zu erstellen.  
  
## <a name="using-properties-to-modify-projects"></a>Verwenden von Eigenschaften zum Ändern von Projekten  
 Das Element `Property` definiert eine Variable, die in einer Projektdatei, z.B. den Speicherort eines temporären Ordners, mehrmals verwiesen wird oder um die Werte für Eigenschaften festzulegen, die in mehrere Konfigurationen (z.B. einem Debug- oder Releasebuild) verwendet werden. Weitere Informationen zu Eigenschaften finden Sie unter [MSBuild-Eigenschaften](msbuild-properties1.md).  
  
 Sie können Eigenschaften verwenden, um die Konfiguration Ihres Builds zu ändern, ohne die Projektdatei zu ändern. Das Attribut `Condition` des Elements `Property` und `PropertyGroup` hilft Ihnen beim Ändern der Eigenschaftenwerte. Weitere Informationen zu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Bedingungen finden Sie unter [Bedingungen](../msbuild/msbuild-conditions.md).  
  
#### <a name="to-set-a-group-of-properties-based-on-another-property"></a>So legen Sie eine Eigenschaftengruppe anhand einer anderen Eigenschaft fest.  
  
-   Verwenden Sie ein Attribut `Condition` in einem Element `PropertyGroup`, das ähnlich dem Folgenden ist:  
  
    ```  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
    ```  
  
#### <a name="to-define-a-property-based-on-another-property"></a>So definieren Sie eine Eigenschaft anhand einer anderen Eigenschaft  
  
-   Verwenden Sie ein Attribut `Condition` im Element `Property`, das ähnlich dem Folgenden ist:  
  
    ```  
    <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>  
    ```  
  
## <a name="specifying-properties-on-the-command-line"></a>Festlegen von Eigenschaften in der Befehlszeile  
 Nachdem die Projektdatei geschrieben wurde und mehrere Konfigurationen zulässt, müssen Sie die Möglichkeit haben, diese Konfigurationen zu ändern, wenn Sie Ihr Projekt erstellen. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bietet diese Möglichkeit, indem es erlaubt Eigenschaften mithilfe des Schalters **/property** oder **/p** in der Befehlszeile anzugeben  
  
#### <a name="to-set-a-project-property-at-the-command-line"></a>So legen Sie eine Projekteigenschaft in der Befehlszeile fest  
  
-   Verwenden Sie den Schalter **/property** mit der Eigenschaft und dem Eigenschaftswert. Zum Beispiel:  
  
    ```  
    msbuild file.proj /property:Flavor=Debug  
    ```  
  
     - ODER  
  
    ```  
    Msbuild file.proj /p:Flavor=Debug  
    ```  
  
#### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>So geben Sie mehr als eine Projekteigenschaft in der Befehlszeile an  
  
-   Verwenden Sie mehrmals den Schalter **/property** oder **/p** mit der Eigenschaft und den Eigenschaftswerten, oder verwenden Sie einen Schalter **/property** bzw. **/p** und unterteilen mehrere Eigenschaft mithilfe des Semikolons (;). Zum Beispiel:  
  
    ```  
    msbuild file.proj /p:Flavor=Debug;Platform=x86  
    ```  
  
     - oder –  
  
    ```  
    msbuild file.proj /p:Flavor=Debug /p:Platform=x86  
    ```  
  
 Umgebungsvariablen werden ebenfalls als Eigenschaften behandelt und automatisch von [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] integriert. Weitere Informationen zur Verwendung von Umgebungsvariablen finden Sie unter [Vorgehensweise: Verwenden von Umgebungsvariablen in einem Build](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
 Der Wert der Eigenschaft, die in der Befehlszeile angegeben ist, hat Vorrang vor jedem Wert, dem in der Projektdatei der gleiche Wert zugewiesen wurde. Dieser Wert hat Vorrang vor dem Wert in einer Umgebungsvariable.  
  
 Sie können dieses Verhalten ändern, indem Sie das Attribut `TreatAsLocalProperty` in einem Projekttag verwenden. Der Eigenschaftswert, der auf der Befehlszeile angegeben wurde, hat für Eigenschaftsnamen, die mit diesem Attribut aufgeführt sind, kein Vorrang vor dem Wert in der Projektdatei. Sie finden ein Beispiel weiter unten in diesem Thema.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel, das Projekt „Hello World“, enthält zwei neue Eigenschaftengruppen, die verwendet werden können, um ein Debugbuild und ein Releasebuild zu erstellen.  
  
 So erstellen Sie die Debugversion des Projekts:  
  
```  
msbuild consolehwcs1.proj /p:flavor=debug  
```  
  
 So erstellen Sie die Verkaufsversion des Projekts:  
  
```  
msbuild consolehwcs1.proj /p:flavor=retail  
```  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <!-- Sets the default flavor of an environment variable called   
    Flavor is not set or specified on the command line -->  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
    </PropertyGroup>  
  
    <!-- Define the DEBUG settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
  
    <!-- Define the RETAIL settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>yes</Optimize>  
    </PropertyGroup>  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldCS</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input files  
        of type CSFile -->  
        <CSC  Sources = "@(CSFile)"  
            DebugType="$(DebugType)"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe" >  
  
            <!-- Set the OutputAssembly attribute of the CSC  
            task to the name of the executable file that is   
            created -->  
            <Output TaskParameter="OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht, wie das Attribut `TreatAsLocalProperty` verwendet wird. Die Eigenschaft `Color` hat den Wert `Blue` in der Projektdatei und `Green` in der Befehlszeile. Mit `TreatAsLocalProperty="Color"` im Projekttag setzt die Befehlszeileneigenschaft (`Green`) nicht die Eigenschaft außer Kraft, die in der Projektdatei definiert ist (`Blue`).  
  
 Geben Sie zum Erstellen des Projekts den folgenden Befehl ein:  
  
```  
msbuild colortest.proj /t:go /property:Color=Green  
```  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0" TreatAsLocalProperty="Color">  
  
    <PropertyGroup>  
        <Color>Blue</Color>  
    </PropertyGroup>  
  
    <Target Name="go">  
        <Message Text="Color: $(Color)" />  
    </Target>  
</Project>  
  
<!--  
  Output with TreatAsLocalProperty="Color" in project tag:  
     Color: Blue  
  
  Output without TreatAsLocalProperty="Color" in project tag:  
     Color: Green  
-->  
```  
  
## <a name="see-also"></a>Siehe auch  
[MSBuild](msbuild.md)  
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)  (MSBuild-Grundlagen)  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [Project-Element (MSBuild)](../msbuild/project-element-msbuild.md)


