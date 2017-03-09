---
title: "Project-Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Project"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ToolsVersion-Attribut [MSBuild]"
  - "< Project >-Element [MSBuild]"
  - "Project-Element [MSBuild]"
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
caps.latest.revision: 31
caps.handback.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Project-Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] -Projektdatei.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>  
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Choose>... </Choose>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Target>... </Target>  
    <UsingTask.../>  
    <ProjectExtensions>... </ProjectExtensions>  
    <Import... />  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`DefaultTargets`|Optionales Attribut.<br /><br /> Der Standardwert oder Ziele, die den Einstiegspunkt des Builds werden, wenn kein Ziel angegeben wurde. Mehrere Ziele werden durch Semikolons (;) getrennt.<br /><br /> Wenn kein Standardziel angegeben ist die `DefaultTargets` Attribut oder [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Befehlszeile führt das Modul das erste Ziel in der Projektdatei nach der [importieren](../msbuild/import-element-msbuild.md) Elemente ausgewertet wurden.|  
|`InitialTargets`|Optionales Attribut.<br /><br /> Die anfängliche oder Ziele, bevor die im angegebenen Ziele ausgeführt werden, die `DefaultTargets` Attribut oder in der Befehlszeile. Mehrere Ziele werden durch Semikolons (;) getrennt.|  
|`ToolsVersion`|Optionales Attribut.<br /><br /> Die Version des MSBuild-Toolsets verwendet, um die Werte für $(MSBuildBinPath) und (MSBuildToolsPath) zu bestimmen.|  
|`TreatAsLocalProperty`|Optionales Attribut.<br /><br /> Eigenschaftennamen, die betrachtet wird nicht global ist. Dieses Attribut wird verhindert, dass bestimmte Befehlszeileneigenschaften überschreiben Eigenschaftswerte, die in einer Projekts oder der Targets-Datei und alle nachfolgenden Importen festgelegt werden. Mehrere Eigenschaften werden durch Semikolons (;) getrennt.<br /><br /> Globale Eigenschaften überschreiben normalerweise Eigenschaftswerte, die in der Projekts oder der Targets-Datei festgelegt werden. Wenn die Eigenschaft, in aufgeführt wird der `TreatAsLocalProperty` -Wert, den Wert der globalen Eigenschaft außer Kraft Eigenschaftswerte, die in dieser Datei und alle nachfolgenden Importen festgelegt werden. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen identischer Quelldateien mit unterschiedlichen Optionen](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Hinweis:**  Festlegen globaler Eigenschaften an der Befehlszeile mithilfe der **Befehlszeilenschalter/Property** (oder **/p**) wechseln. Sie können auch festlegen, oder ändern Sie globale Eigenschaften für untergeordnete Projekte in einem Build mit mehreren Projekten mithilfe der `Properties` -Attribut der MSBuild-Aufgabe. Weitere Informationen finden Sie unter [MSBuild-Aufgabe](../msbuild/msbuild-task.md).|  
|`Xmlns`|Erforderliches Attribut.<br /><br /> Die `xmlns` Attribut muss den Wert "http://schemas.microsoft.com/developer/msbuild/2003" haben.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Wählen Sie](../msbuild/choose-element-msbuild.md)|Optionales Element.<br /><br /> Wertet untergeordnete Elemente markieren Sie einen Satz von `ItemGroup` Elemente und/oder `PropertyGroup` Elemente ausgewertet.|  
|[Importieren](../msbuild/import-element-msbuild.md)|Optionales Element.<br /><br /> Ermöglicht eine Projektdatei in eine andere Projektdatei importieren. Möglicherweise gibt es 0 (null) oder mehr `Import` Elemente in einem Projekt.|  
|[ItemGroup-Element](../msbuild/itemgroup-element-msbuild.md)|Optionales Element.<br /><br /> Ein Gruppierungselement für einzelne Elemente. Elemente werden angegeben, mit der [Element](../msbuild/item-element-msbuild.md) Element. Möglicherweise gibt es 0 (null) oder mehr `ItemGroup` Elemente in einem Projekt.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|Optionales Element.<br /><br /> Bietet eine Möglichkeit, die nicht beibehalten[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Informationen in einem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] -Projektdatei. Möglicherweise gibt es 0 (null) oder eine `ProjectExtensions` Elemente in einem Projekt.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Optionales Element.<br /><br /> Ein Gruppierungselement für einzelne Eigenschaften. Eigenschaften werden angegeben, mit der [Eigenschaft](../msbuild/property-element-msbuild.md) Element. Möglicherweise gibt es 0 (null) oder mehr `PropertyGroup` Elemente in einem Projekt.|  
|[Ziel](../msbuild/target-element-msbuild.md)|Optionales Element.<br /><br /> Enthält eine Reihe von Aufgaben für [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sequenziell ausführen. Aufgaben werden angegeben, mit der [Aufgabe](../msbuild/task-element-msbuild.md) Element. Möglicherweise gibt es 0 (null) oder mehr `Target` Elemente in einem Projekt.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Optionales Element.<br /><br /> Bietet eine Möglichkeit, Aufgaben in registriert [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Möglicherweise gibt es 0 (null) oder mehr `UsingTask` Elemente in einem Projekt.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
 Keine  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Angeben des zuerst zu erstellenden Ziels](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md)   
 [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild1.md)