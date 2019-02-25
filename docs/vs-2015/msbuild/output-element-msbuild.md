---
title: Output-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 327f65ef6639f444326d59d6db990e9c732a760f
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54790282"
---
# <a name="output-element-msbuild"></a>Output-Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Speichert Aufgabenausgabewerte in Elementen und Eigenschaften.  
  
 \<Project>  
 \<Target>  
 \<Task>  
 \<Output>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`TaskParameter`|Erforderliches Attribut.<br /><br /> Der Name des Ausgabeparameters der Aufgabe.|  
|`PropertyName`|Entweder ist Attribut `PropertyName` oder Attribut `ItemName` erforderlich.<br /><br /> Die Eigenschaft, die den Ausgabeparameterwert der Aufgabe empfängt. Das Projekt kann dann mit der `$(`*PropertyName*`)`-Syntax auf die Eigenschaft verweisen. Dieser Eigenschaftsname kann entweder ein neuer Eigenschaftsname oder ein Name sein, der bereits im Projekt definiert ist.<br /><br /> Dieses Attribut kann nicht verwendet werden, wenn `ItemName` auch verwendet wird.|  
|`ItemName`|Entweder ist Attribut `PropertyName` oder Attribut `ItemName` erforderlich.<br /><br /> Das Element, das den Ausgabeparameterwert der Aufgabe empfängt. Das Projekt kann dann mit der `@(`*ItemName*`)`-Syntax auf das Element verweisen. Der Name des Elements kann entweder ein neuer Elementname oder ein Name sein, der bereits im Projekt definiert ist.<br /><br /> Dieses Attribut kann nicht verwendet werden, wenn `PropertyName` auch verwendet wird.|  
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Aufgabe](../msbuild/task-element-msbuild.md)|Erstellt und führt eine Instanz einer [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Aufgabe aus.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt die Ausführung einer `Csc`-Aufgabe innerhalb eines `Target`-Elements. Die Elemente und Eigenschaften, die den Aufgabeparametern übergeben werden, werden außerhalb des Bereichs dieses Beispiels deklariert. Der Wert des Ausgabeparameters `OutputAssembly` wird im `FinalAssemblyName`-Element gespeichert, und der Wert des Ausgabeparameters `BuildSucceeded` wird in der `BuildWorked`-Eigenschaft gespeichert. Weitere Informationen finden Sie unter [MSBuild-Aufgaben](../msbuild/msbuild-tasks.md).  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)   
 [Aufgaben](../msbuild/msbuild-tasks.md)
