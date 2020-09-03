---
title: Task-Element (MSBuild) | Microsoft-Dokumentation
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
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6683aac3c5a4314df6fde3d72dd9085b6608d8a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202266"
---
# <a name="task-element-msbuild"></a>Aufgabenelement (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erstellt und führt eine Instanz einer [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Aufgabe aus. Der Elementname wird durch den Namen der erstellten Aufgabe bestimmt.  
  
 \<Project>  
 \<Target>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Condition`|Optionales Attribut. Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|  
|`ContinueOnError`|Optionales Attribut. Kann einen oder mehrere der folgenden Werte enthalten:<br /><br /> -   **Warnandcontinue** oder **true**. Wenn ein Task fehlschlägt, werden nachfolgende Aufgaben im [Ziel](../msbuild/target-element-msbuild.md) Element und im Build weiterhin ausgeführt, und alle Fehler aus der Aufgabe werden als Warnungen behandelt.<br />-   **Errorandcontinue**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element `Target` und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Fehler behandelt.<br />-   **Errorandstopps** oder **false** (Standard). Wenn eine Aufgabe fehlschlägt, werden die übrigen Aufgaben im Element `Target` und im Build nicht ausgeführt, und das komplette Element `Target` sowie der Build wird als fehlgeschlagen betrachtet.<br /><br /> Versionen von .NET Framework vor 4.5 unterstützten nur die Werte `true` und `false`.<br /><br /> Weitere Informationen finden Sie unter [Gewusst wie: Ignorieren von Fehlern in Aufgaben](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Erforderlich, wenn die Aufgabenklasse eine oder mehrere Eigenschaften enthält, die mit dem `[Required]`-Attribut gekennzeichnet sind.<br /><br /> Ein benutzerdefinierter Aufgabenparameter, der den Parameterwert als Wert enthält. Das `Task`-Element kann eine beliebige Anzahl von Parametern enthalten, wobei jedes Attribut einer .NET-Eigenschaft in der Aufgabenklasse zugeordnet ist.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Ausgabe](../msbuild/output-element-msbuild.md)|Speichert die Ausgaben der Aufgabe in der Projektdatei. Die Aufgabe kann keine oder mehrere `Output`-Elemente enthalten.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Ziel](../msbuild/target-element-msbuild.md)|Containerelement für [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Aufgaben.|  
  
## <a name="remarks"></a>Bemerkungen  
 Ein `Task`-Element in einer [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projektdatei erstellt eine Instanz einer Aufgabe, legt entsprechende Eigenschaften fest und führt sie aus. Das `Output`-Element speichert Ausgabeparameter in Eigenschaften oder Elementen, damit sie an anderer Stelle in der Projektdatei verwendet werden können.  
  
 Auch bei [OnError](../msbuild/onerror-element-msbuild.md)-Elementen im übergeordneten `Target`-Element einer Aufgabe werden sie ausgewertet, wenn die Aufgabe fehlschlägt und `ContinueOnError` den Wert `false` aufweist. Weitere Informationen zu Aufgaben finden Sie unter [Aufgaben](../msbuild/msbuild-tasks.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel erstellt eine Instanz der [Csc-Aufgabenklasse](../msbuild/csc-task.md), legt sechs Eigenschaften fest und führt die Aufgabe aus. Nach der Ausführung wird der Wert der `OutputAssembly`-Eigenschaft des Objekts in eine Liste mit dem Namen `FinalAssemblyName` aufgenommen.  
  
```  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erfüllen](../msbuild/msbuild-tasks.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)   
 [Referenz zum Projektdatei Schema](../msbuild/msbuild-project-file-schema-reference.md)
