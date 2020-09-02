---
title: Referenz zum MSBuild-Projektdateischema | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 847fa53acad63cec151222521ed8f85090c52080
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158853"
---
# <a name="msbuild-project-file-schema-reference"></a>Referenz zum MSBuild-Projektdateischema
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Enthält eine Tabelle mit allen XML-Schemaelementen von [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] sowie ihren verfügbaren Attributen und untergeordneten Elementen.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] verwendet Projektdateien, um der Build-Engine anzuzeigen, was wie erstellt werden soll. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projektdateien sind XML-Dateien, für die das [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-XML-Schema gilt. Dieser Abschnitt beschreibt die XML-Schemadefinitionsdatei (XSD) für [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
## <a name="msbuild-xml-schema-elements"></a>XML-Schemaelemente von MSBuild  
 Die folgende Tabelle enthält alle XML-Schemaelemente von [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] sowie die untergeordneten Elemente und Attribute.  
  
|Element|Untergeordnete Elemente|Attribute|  
|-------------|--------------------|----------------|  
|[Choose-Element (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> When|--|  
|[Import-Element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Bedingung<br /><br /> Project|  
|[Importgroup-Element](../msbuild/importgroup-element.md)|Importieren|Bedingung|  
|[Item-Element (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Bedingung<br /><br /> Exclude<br /><br /> Einschließen<br /><br /> Entfernen|  
|[ItemDefinitionGroup-Element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Element*|Bedingung|  
|[ItemGroup-Element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Element*|Bedingung|  
|[ItemMetadata-Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Element*|Bedingung|  
|[OnError-Element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Bedingung<br /><br /> ExecuteTargets|  
|[Andernfalls-Element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Output-Element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Bedingung<br /><br /> Artikelname<br /><br /> PropertyName<br /><br /> TaskParameter|  
|[Parameter-Element](../msbuild/parameter-element.md)|--|Output<br /><br /> ParameterType<br /><br /> Erforderlich|  
|[Parametergroup-Element](../msbuild/parametergroup-element.md)|*Parameter*|--|  
|[Project-Element (MSBuild)](../msbuild/project-element-msbuild.md)|Choose<br /><br /> Importieren<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Ziel<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|  
|[ProjectExtensions-Element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Property-Element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Bedingung|  
|[PropertyGroup Element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Eigenschaft*|Bedingung|  
|[Target-Element (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Aufgabe*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Bedingung<br /><br /> DependsOnTargets<br /><br /> Eingaben<br /><br /> KeepDuplicateOutputs<br /><br /> Name<br /><br /> Ausgaben<br /><br /> Gibt zurück|  
|[Task-Element (MSBuild)](../msbuild/task-element-msbuild.md)|Output|Bedingung<br /><br /> ContinueOnError<br /><br /> *Parameter*|  
|[TaskBody-Element (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Daten*|Evaluieren|  
|[UsingTask-Element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile<br /><br /> AssemblyName<br /><br /> Bedingung<br /><br /> TaskFactory<br /><br /> TaskName|  
|[When-Element (MSBuild)](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|Bedingung|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)   
 [Voraus](../msbuild/msbuild-conditions.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)
