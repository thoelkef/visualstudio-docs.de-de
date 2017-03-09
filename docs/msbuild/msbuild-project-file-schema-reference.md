---
title: "Referenz zum MSBuild-Projektdateischema | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild-Dateischema"
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Referenz zum MSBuild-Projektdateischema
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Enthält eine Tabelle mit allen der [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] XML-Schemaelemente und die verfügbaren Attribute und untergeordneten Elementen.  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Mithilfe von Projektdateien auf dem was erstellen und wie Sie es erstellen Buildmodul. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Projektdateien sind XML-Dateien, die folgen, der [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] XML-Schema. Dieser Abschnitt beschreibt die XML-Schema Definition (XSD) Datei [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## <a name="msbuild-xml-schema-elements"></a>MSBuild-XML-Schema-Elemente  
 Die folgende Tabelle listet alle von der [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] XML-Schemaelemente sowie die untergeordneten Elemente und Attribute.  
  
|Element|Untergeordnete Elemente|Attribute|  
|-------------|--------------------|----------------|  
|[Choose-Element (MSBuild)](../msbuild/choose-element-msbuild.md)|Andernfalls<br /><br /> When|--|  
|[Import-Element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Bedingung<br /><br /> Projekt|  
|[ImportGroup-Element](../msbuild/importgroup-element.md)|Importieren|Bedingung|  
|[Item-Element (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Bedingung<br /><br /> Ausschließen<br /><br /> Einschließen<br /><br /> Remove|  
|[ItemDefinitionGroup-Element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Element*|Bedingung|  
|[ItemGroup-Element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Element*|Bedingung|  
|[ItemMetadata-Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Element*|Bedingung|  
|[OnError-Element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Bedingung<br /><br /> ExecuteTargets|  
|[Otherwise-Element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Wählen<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Output-Element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Bedingung<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|  
|[Parameter-Element](../msbuild/parameter-element.md)|--|Ausgabe<br /><br /> ParameterType<br /><br /> Erforderlich|  
|[ParameterGroup-Element](../msbuild/parametergroup-element.md)|*Parameter*|--|  
|[Project-Element (MSBuild)](../msbuild/project-element-msbuild.md)|Wählen<br /><br /> Importieren<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Ziel<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|  
|[ProjectExtensions-Element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Property-Element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Bedingung|  
|[PropertyGroup-Element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Eigenschaft*|Bedingung|  
|[Target-Element (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Aufgabe*|AfterTargets<br /><br /> Des BeforeTargets<br /><br /> Bedingung<br /><br /> DependsOnTargets<br /><br /> Eingaben<br /><br /> KeepDuplicateOutputs<br /><br /> Name<br /><br /> Ausgaben<br /><br /> Rückgabe|  
|[Task-Element (MSBuild)](../msbuild/task-element-msbuild.md)|Ausgabe|Bedingung<br /><br /> ContinueOnError<br /><br /> *Parameter*|  
|[TaskBody-Element (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Daten*|Auswerten|  
|[UsingTask-Element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile<br /><br /> AssemblyName<br /><br /> Bedingung<br /><br /> TaskFactory<br /><br /> TaskName|  
|[Wenn Element (MSBuild)](../msbuild/when-element-msbuild.md)|Wählen<br /><br /> ItemGroup<br /><br /> PropertyGroup|Bedingung|  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu Aufgaben](../msbuild/msbuild-task-reference.md)   
 [Bedingungen](../msbuild/msbuild-conditions.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild1.md)