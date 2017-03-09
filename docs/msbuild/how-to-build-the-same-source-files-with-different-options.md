---
title: "Gewusst wie: Erstellen identischer Quelldateien mit unterschiedlichen Optionen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Quelldateien erstellen mit unterschiedlichen Optionen"
  - "MSBuild-Eigenschaften"
  - "Ändern von Projekteigenschaften"
  - "Hello World-Beispiel [Visual Studio]"
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Erstellen identischer Quelldateien mit unterschiedlichen Optionen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie Projekte erstellen, kompilieren Sie häufig die gleichen Komponenten mit unterschiedlichen Buildoptionen. Beispielsweise können Sie einen Debugbuild mit Symbolinformationen oder ein Releasebuild ohne Symbolinformationen aber mit aktivierten Optimierungen erstellen. Oder Sie können ein Projekt erstellen, führen Sie auf einer bestimmten Plattform, z. B. X86 oder [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)]. In allen diesen Fällen bleiben die meisten Buildoptionen identisch. nur einige Optionen werden zur Steuerung der Buildkonfiguration geändert. Mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], Sie die Eigenschaften und Bedingungen verwenden, um die verschiedenen Buildkonfigurationen erstellen.  
  
## <a name="using-properties-to-modify-projects"></a>Verwenden von Eigenschaften zum Ändern von Projekten  
 Das `Property` -Element definiert eine Variable, die in einer Projektdatei, z. B. den Speicherort eines temporären Ordners, mehrmals verwiesen wird, oder um die Werte für Eigenschaften festzulegen, die in verwendet werden mehrere Konfigurationen, wie ein Debugbuild und eine Version erstellen. Weitere Informationen zu Eigenschaften finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).  
  
 Sie können Eigenschaften verwenden, um die Konfiguration des Builds zu ändern, ohne die Projektdatei ändern. Das `Condition` -Attribut des der `Property` Element und die `PropertyGroup` Element können Sie den Wert der Eigenschaften zu ändern. Weitere Informationen zu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Umständen finden Sie unter [Bedingungen](../msbuild/msbuild-conditions.md).  
  
#### <a name="to-set-a-group-of-properties-based-on-another-property"></a>Eine Gruppe von Eigenschaften, die auf Grundlage einer anderen Eigenschaft festlegen  
  
-   Verwenden einer `Condition` Attribut in einer `PropertyGroup` ähnlich dem folgenden Element:  
  
    ```  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
    ```  
  
#### <a name="to-define-a-property-based-on-another-property"></a>Eine Eigenschaft, die basierend auf einer anderen Eigenschaft definieren  
  
-   Verwenden einer `Condition` Attribut in einer `Property` ähnlich dem folgenden Element:  
  
    ```  
    <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>  
    ```  
  
## <a name="specifying-properties-on-the-command-line"></a>Angeben von Eigenschaften in der Befehlszeile  
 Nachdem die Projektdatei geschrieben wurde und mehrere Konfigurationen zulässt, müssen Sie haben die Möglichkeit, diese Konfigurationen zu ändern, wenn Sie das Projekt erstellen. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bietet diese Möglichkeit, indem Eigenschaften in der Befehlszeile angegeben werden die **Befehlszeilenschalter/Property** oder **/p** wechseln.  
  
#### <a name="to-set-a-project-property-at-the-command-line"></a>Eine Projekteigenschaft in der Befehlszeile fest  
  
-   Verwenden der **Befehlszeilenschalter/Property** Wechseln Sie mit der Eigenschaft und dem Eigenschaftswert. Zum Beispiel:  
  
    ```  
    msbuild file.proj /property:Flavor=Debug  
    ```  
  
     - ODER  
  
    ```  
    Msbuild file.proj /p:Flavor=Debug  
    ```  
  
#### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Mehr als eine Eigenschaft in der Befehlszeile angeben.  
  
-   Verwenden Sie die **Befehlszeilenschalter/Property** oder **/p** mehrere Male mit der Eigenschaft und die Eigenschaftswerte zu wechseln, oder verwenden Sie eine **Befehlszeilenschalter/Property** oder **/p** wechseln, und trennen Sie mehrere Eigenschaften mithilfe von Semikolons (;). Zum Beispiel:  
  
    ```  
    msbuild file.proj /p:Flavor=Debug;Platform=x86  
    ```  
  
     - oder -  
  
    ```  
    msbuild file.proj /p:Flavor=Debug /p:Platform=x86  
    ```  
  
 Umgebungsvariablen werden ebenfalls als Eigenschaften behandelt und automatisch von integriert [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Weitere Informationen zur Verwendung von Umgebungsvariablen finden Sie unter [Gewusst wie: Verwenden von Umgebungsvariablen in einem Build](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
 Der Wert der Eigenschaft, der in der Befehlszeile angegeben wird Vorrang vor allen anderen Werten, die für die gleiche Eigenschaft in der Projektdatei festgelegt ist, der Wert in der Projektdatei Vorrang vor den Wert in einer Umgebungsvariablen.  
  
 Sie können dieses Verhalten ändern, indem Sie mit der `TreatAsLocalProperty` Attribut in einem Projekttag. Eigenschaftsnamen, die mit diesem Attribut aufgeführt sind, Vorrang nicht den Wert der Eigenschaft, der in der Befehlszeile angegeben wird der Wert in der Datei. Ein Beispiel finden weiter unten in diesem Thema.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird das Projekt "Hello World" enthält zwei neue Eigenschaftengruppen, die verwendet werden können, um einen Debugbuild und einem Releasebuild zu erstellen.  
  
 Um die Debugversion des Projekts zu erstellen, geben Sie Folgendes ein:  
  
```  
msbuild consolehwcs1.proj /p:flavor=debug  
```  
  
 Um die Verkaufsversion von diesem Projekt zu erstellen, geben Sie Folgendes ein:  
  
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
 Das folgende Beispiel zeigt, wie die `TreatAsLocalProperty` Attribut. Die `Color` Eigenschaft kann einen Wert von `Blue` in der Projektdatei und `Green` in der Befehlszeile. Mit `TreatAsLocalProperty="Color"` im Projekttag die Befehlszeileneigenschaft (`Green`) nicht außer Kraft setzen die Eigenschaft, die in der Projektdatei definiert ist (`Blue`).  
  
 Um das Projekt zu erstellen, geben Sie den folgenden Befehl ein:  
  
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
[MSBuild](../msbuild/msbuild1.md)  
 [MSBuild-Konzepte](../msbuild/msbuild-concepts.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
 [Project-Element (MSBuild)](../msbuild/project-element-msbuild.md)