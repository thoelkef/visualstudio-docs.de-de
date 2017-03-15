---
title: Project-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
caps.latest.revision: 31
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 203e1e27cc892e96b103fc6cb22a73672a8e16af
ms.openlocfilehash: 224371f6915258a9860c5f05554445f6b1ae106c
ms.lasthandoff: 03/01/2017

---
# <a name="project-element-msbuild"></a>Project-Element (MSBuild)
Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projektdatei.  

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
|`DefaultTargets`|Optionales Attribut.<br /><br /> Das Standardziel oder die Standardziele, die zum Einstiegspunkt des Builds werden, wenn kein Ziel angegeben wurde. Mehrere Ziele werden durch Semikolons (;) getrennt.<br /><br /> Wenn kein Standardziel im `DefaultTargets`-Attribut oder der [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Befehlszeile angegeben ist, führt das Modul das erste Ziel in der Projektdatei aus, nachdem die [Import](../msbuild/import-element-msbuild.md)-Elemente ausgewertet wurden.|  
|`InitialTargets`|Optionales Attribut.<br /><br /> Die anfänglichen Ziele werden ausgeführt bevor die Ziele im `DefaultTargets`-Attribut oder in der Befehlszeile angegeben werden . Mehrere Ziele werden durch Semikolons (;) getrennt.|  
|`SDK`|Optionales Attribut. (Nur für .NET Core-Projekte in Visual Studio 2017 oder höher verfügbar.)<br /><br /> Die SDK-Version, die zum Erstellen impliziter Import-Anweisungen verwendet wird, die der PROJ-Datei hinzugefügt werden. Beispielsweise `<Project Sdk="Microsoft.NET.Sdk/1.0.0-RC" />`.|  
|`ToolsVersion`|Optionales Attribut.<br /><br /> Die Version des Toolsets, das MSBuild verwendet, um die Werte für $(MSBuildBinPath) und (MSBuildToolsPath) zu bestimmen.|  
|`TreatAsLocalProperty`|Optionales Attribut.<br /><br /> Eigenschaftennamen, die nicht als global betrachtet werden. Dieses Attribut verhindert, dass bestimmte Befehlszeileneigenschaften Eigenschaftswerte überschreiben, die in einer Projekt- oder Zieldatei und allen nachfolgenden Importen festgelegt sind. Mehrere Eigenschaften werden durch Semikolons (;) getrennt.<br /><br /> Diese globalen Eigenschaften überschreiben normalerweise Eigenschaftswerte, die in der Projektdatei oder in Zieldateien festgelegt werden. Wenn die Eigenschaft im `TreatAsLocalProperty`-Wert aufgeführt wird, überschreibt der globale Eigenschaftenwert die Eigenschaftenwerte nicht, die in dieser Datei und allen nachfolgenden Importen festgelegt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen identischer Quelldateien mit unterschiedlichen Optionen](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Hinweis:** Festlegen globaler Eigenschaften in der Befehlszeile mithilfe des Schalters **/property** (oder **/p**). Globale Eigenschaften können auch für untergeordnete Projekte in einem Build mit mehreren Projekten festgelegt oder geändert werden, indem das `Properties`-Attribut der MSBuild-Aufgabe verwendet wird. Weitere Informationen finden Sie unter [MSBuild-Aufgabe](../msbuild/msbuild-task.md).|  
|`Xmlns`|Optionales Attribut.<br /><br /> Wenn angegeben, muss das `xmlns`-Attribut den Wert „http://schemas.microsoft.com/developer/msbuild/2003“ haben.|  

### <a name="child-elements"></a>Untergeordnete Elemente  

|Element|Beschreibung|  
|-------------|-----------------|  
|[Auswählen](../msbuild/choose-element-msbuild.md)|Optionales Element.<br /><br /> Bewertet untergeordnete Elemente, um einen Satz von auszuwertenden `ItemGroup`-Elementen und/oder `PropertyGroup`-Elementen auszuwählen.|  
|[Importieren](../msbuild/import-element-msbuild.md)|Optionales Element.<br /><br /> Ermöglicht den Import einer Projektdatei in eine andere Projektdatei. Es kann kein oder mehrere `Import`-Elemente in einem Projekt geben.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Optionales Element.<br /><br /> Ein Gruppierungselement für einzelne Elemente. Elemente werden mit dem [Item](../msbuild/item-element-msbuild.md)-Element angegeben. Es kann kein oder mehrere `ItemGroup`-Elemente in einem Projekt geben.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|Optionales Element.<br /><br /> Bietet eine Möglichkeit, die nicht-[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Informationen in einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projektdatei beizubehalten. Es kann kein oder mehrere `ProjectExtensions`-Elemente in einem Projekt geben.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Optionales Element.<br /><br /> Ein Gruppierungselement für einzelne Eigenschaften. Eigenschaften werden mit dem [Property](../msbuild/property-element-msbuild.md)-Element angegeben. Es kann kein oder mehrere `PropertyGroup`-Elemente in einem Projekt geben.|  
|[Ziel](../msbuild/target-element-msbuild.md)|Optionales Element.<br /><br /> Enthält eine Reihe von Aufgaben, die [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sequenziell ausführt. Aufgaben werden mit dem [Aufgaben](../msbuild/task-element-msbuild.md)-Element angegeben. Es kann kein oder mehrere `Target`-Elemente in einem Projekt geben.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Optionales Element.<br /><br /> Bietet eine Möglichkeit, Aufgaben in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zu registrieren. Es kann kein oder mehrere `UsingTask`-Elemente in einem Projekt geben.|  

### <a name="parent-elements"></a>Übergeordnete Elemente  
 Keine  

## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Angeben des zuerst zu erstellenden Ziels](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md)   
 [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)

