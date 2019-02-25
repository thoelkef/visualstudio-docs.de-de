---
title: Parameter-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4c53528159d2950378c56e1da22d81393235f716
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54803381"
---
# <a name="parameter-element"></a>Parameter-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Enthält Informationen über einen bestimmten Parameter für eine Aufgabe, die von einer `UsingTask``TaskFactory` generiert wird.  Der Name des Elements ist der Name des Parameters.  Weitere Informationen finden Sie unter [UsingTask-Element (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
 \<Parameter>  
  
## <a name="syntax"></a>Syntax  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`ParameterType`|Optionales Attribut.<br /><br /> Der .NET-Typ des Parameters, z.B. „System.String“.|  
|`Output`|Optionales boolesches Attribut.<br /><br /> Wenn `true`, ist dieser Parameter ein Ausgabeparameter für die Aufgabe. In der Standardeinstellung ist der Wert `false`.|  
|`Required`|Optionales boolesches Attribut.<br /><br /> Wenn `true`, ist dieser Parameter ein erforderlicher Parameter für die Aufgabe. In der Standardeinstellung ist der Wert `false`.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Enthält eine optionale Liste von Parametern, die für die Aufgabe vorhanden sein werden, die von `UsingTask``TaskFactory` generiert wird.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung des `Parameter`-Elements veranschaulicht.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Referenz zum MSBuild-Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
