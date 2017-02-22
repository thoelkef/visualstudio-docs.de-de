---
title: "T4 Assembly Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44949749-ce3c-4fb5-8690-a17f1564ac2f
caps.latest.revision: 4
caps.handback.revision: 4
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 Assembly Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Entwurfszeittextvorlage wird mit der `assembly`\-Direktive eine Assembly geladen, damit im Vorlagencode die Typen der Vorlage verwendet werden können.  Der Effekt ist mit dem Hinzufügen eines Assemblyverweises in einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekt vergleichbar.  
  
 Eine allgemeine Übersicht über das Schreiben von Textvorlagen finden Sie unter [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  Die `assembly`\-Direktive ist in einer Laufzeitvorlage \(vorverarbeiteten Vorlage\) nicht erforderlich.  Fügen Sie den **Verweisen** des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekts stattdessen die notwendigen Assemblys hinzu.  
  
## Verwenden der Assemblydirektive  
 Die Syntax der Direktive lautet wie folgt:  
  
```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 Folgende Optionen stehen zum Angeben des Assemblynamens zur Verfügung:  
  
-   Der starke Name einer Assembly im GAC, z. B. `System.Xml.dll`.  Sie können auch das lange Formular verwenden, z. B. `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`.  Weitere Informationen finden Sie unter <xref:System.Reflection.AssemblyName>.  
  
-   Absoluter Pfad der Assembly  
  
 Sie können mit der `$(variableName)`\-Syntax auf [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Variablen wie `$(SolutionDir)` und mit `%VariableName%` auf Umgebungsvariablen verweisen.  Beispiel:  
  
```  
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>  
```  
  
 Die assembly\-Direktive hat in einer vorverarbeiteten Textvorlage keinerlei Auswirkungen.  Schließen Sie stattdessen die notwendigen Verweise in den Abschnitt **Verweise** des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekts ein.  Weitere Informationen finden Sie unter [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## Standardassemblys  
 Die folgenden Assemblys werden automatisch geladen, damit Sie keine Assemblydirektiven dafür schreiben müssen:  
  
-   `Microsoft.VisualStudio.TextTemplating.1*.dll`  
  
-   `System.dll`  
  
-   `WindowsBase.dll`  
  
 Wenn Sie eine benutzerdefinierte Direktive verwenden, lädt der Direktivenprozessor möglicherweise zusätzliche Assemblys.  Wenn Sie z. B. Vorlagen für eine domänenspezifische Sprache \(DSL\) schreiben, müssen Sie keine Assemblydirektiven für die folgenden Assemblys schreiben:  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`  
  
-   `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`  
  
-   Die Assembly mit der DSL.  
  
##  <a name="msbuild"></a> Verwenden von Projekteigenschaften in MSBuild und Visual Studio  
 Visual Studio\-Makros wie $ \(SolutionDir\) funktionieren nicht in MSBuild.  Wenn Sie Vorlagen im Buildcomputer transformieren möchten, müssen Sie dies mithilfe von Projekteigenschaften tun.  
  
 Bearbeiten Sie die CSPROJ\- oder VBPROJ\-Datei, und definieren Sie eine Projekteigenschaft.  In folgendem Beispiel wird eine Eigenschaft mit dem Namen `myLibFolder` definiert:  
  
```xml  
<!-- Define a project property, myLibFolder: -->  
<PropertyGroup>  
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myLibFolder">  
      <Value>$(myLibFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Nun können Sie die Projekteigenschaft in Textvorlagen verwenden, die sowohl in Visual Studio als auch in MSBuild ordnungsgemäß transformiert werden:  
  
```  
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>  
```  
  
## Siehe auch  
 [T4 Include Directive](../modeling/t4-include-directive.md)