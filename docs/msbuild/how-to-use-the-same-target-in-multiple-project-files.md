---
title: "How to: Use the Same Target in Multiple Project Files | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, importing"
  - "MSBuild, using the same target in multiple project files"
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# How to: Use the Same Target in Multiple Project Files
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Falls Sie mehrere [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projektdateien erstellt haben, haben Sie möglicherweise festgestellt, dass die gleichen Aufgaben und Ziele in verschiedenen Projektdateien verwendet werden müssen.  Anstatt die gesamte Beschreibung dieser Aufgaben oder Ziele in jede Projektdatei aufzunehmen, können Sie ein Ziel in einer separaten Projektdatei speichern und dieses Projekt dann in ein anderes Projekt importieren, das das jeweilige Ziel verwenden muss.  
  
## Verwenden des Import\-Elements  
 Das `Import`\-Element wird verwendet, um eine Projektdatei in eine andere Projektdatei einzufügen.  Die importierte Projektdatei muss eine gültige [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projektdatei sein und wohlgeformtes XML enthalten.  Das `Project`\-Attribut gibt den Pfad zur importierten Projektdatei an.  Weitere Informationen zum `Import`\-Element finden Sie unter [Import\-Element \(MSBuild\)](../msbuild/import-element-msbuild.md).  
  
#### So importieren Sie ein Projekt  
  
1.  Definieren Sie in der importierenden Projektdatei alle Eigenschaften und Elemente, die als Parameter für Eigenschaften und Elemente im importierten Projekt verwendet werden.  
  
2.  Verwenden Sie das `Import`\-Element, um das Projekt zu importieren.  Beispiel:  
  
     `<Import Project="MyCommon.targets"/>`  
  
3.  Definieren Sie nach dem `Import`\-Element alle Eigenschaften und Elemente, mit denen die Standarddefinitionen der Eigenschaften und Elemente im importierten Projekt überschrieben werden müssen.  
  
## Reihenfolge der Auswertung  
 Sobald [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ein `Import`\-Element erreicht, wird das importierte Projekt an der Position des `Import`\-Elements effektiv in das importierende Projekt eingefügt.  Deshalb kann die Position des `Import`\-Elements die Werte der Eigenschaften und Elemente beeinflussen.  Es ist wichtig, die vom importierten Projekt festgelegten sowie die vom importierten Projekt verwendeten Eigenschaften und Elemente zu verstehen.  
  
 Bei der Projekterstellung werden zunächst alle Eigenschaften und anschließend die Elemente ausgewertet.  Die importierte Projektdatei MyCommon.targets wird beispielsweise durch die folgende XML definiert:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyCommon</Name>  
    </PropertyGroup>  
  
    <Target Name="Go">  
        <Message Text="Name=$(Name)"/>  
    </Target>  
</Project>  
```  
  
 Die Datei MyApp.proj, durch die MyCommon.targets importiert wird, wird durch folgende XML definiert:  
  
```  
<Project  
    DefaultTargets="Go"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyApp</Name>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
 Bei der Projekterstellung wird die folgende Meldung angezeigt:  
  
 `Name="MyCommon"`  
  
 Das Projekt wird importiert, nachdem die Eigenschaft `Name` in MyApp.proj definiert wurde. Die Definition von `Name` in MyCommon.targets überschreibt daher die Definition in MyApp.proj.  Wenn das Projekt importiert wird, bevor die Eigenschaft Name definiert wird, wird folgende Meldung vom Build angezeigt:  
  
 `Name="MyApp"`  
  
#### Verwenden der folgenden Methode beim Importieren von Projekten  
  
1.  Definieren Sie in der Projektdatei alle Eigenschaften und Elemente, die als Parameter für Eigenschaften und Elemente im importierten Projekt verwendet werden.  
  
2.  Importieren Sie das Projekt.  
  
3.  Definieren Sie in der Projektdatei alle Eigenschaften und Elemente, mit denen die Standarddefinitionen der Eigenschaften und Elemente im importierten Projekt überschrieben werden müssen.  
  
## Beispiel  
 Im folgenden Codebeispiel ist die Datei MyCommon.targets dargestellt, die im zweiten Codebeispiel importiert wird.  Die TARGETS\-Datei wertet Eigenschaften aus dem importierenden Projekt aus, um den Build zu konfigurieren.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>  
        <appname>$(MSBuildProjectName)</appname>  
    <PropertyGroup>  
    <Target Name="Build">  
        <Csc Sources="hello.cs"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe"/>  
    </Target>  
</Project>  
```  
  
## Beispiel  
 Im folgenden Codebeispiel wird die Datei MyCommon.targets importiert.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor>RETAIL</Flavor>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
## Siehe auch  
 [Import\-Element \(MSBuild\)](../msbuild/import-element-msbuild.md)   
 [Targets](../msbuild/msbuild-targets.md)