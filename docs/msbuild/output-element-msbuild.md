---
title: Output-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 13
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
ms.sourcegitcommit: 0e5a449ef396e7b9fd23a2c018bdc7f8791b7b38
ms.openlocfilehash: 7a72f1faa5cfda2efb650f037ffdfcab072760c7
ms.lasthandoff: 03/13/2017

---
# <a name="output-element-msbuild"></a>Output-Element (MSBuild)
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
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions (Bedingungen)](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|Beschreibung|  
|-------------|-----------------|  
|[Aufgabe](../msbuild/task-element-msbuild.md)|Erstellt und führt eine Instanz einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Aufgabe aus.|  

## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt die Ausführung einer `Csc`-Aufgabe innerhalb eines `Target`-Elements. Die Elemente und Eigenschaften, die den Aufgabeparametern übergeben werden, werden außerhalb des Bereichs dieses Beispiels deklariert. Der Wert des Ausgabeparameters `OutputAssembly` wird im `FinalAssemblyName`-Element gespeichert, und der Wert des Ausgabeparameters `BuildSucceeded` wird in der `BuildWorked`-Eigenschaft gespeichert. Weitere Informationen finden Sie unter [Tasks](../msbuild/msbuild-tasks.md) (MSBuild-Aufgaben).  

```xml  
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
 [Tasks](../msbuild/msbuild-tasks.md) (MSBuild-Aufgaben)

