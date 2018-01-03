---
title: Task-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: "22"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5ed723c807bc46933d31baa206625e2ea198d5e3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="task-element-msbuild"></a>Aufgabenelement (MSBuild)
Erstellt und führt eine Instanz einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Aufgabe aus. Der Elementname wird durch den Namen der erstellten Aufgabe bestimmt.  

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

|Attribut|description|  
|---------------|-----------------|  
|`Condition`|Optionales Attribut. Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|  
|`ContinueOnError`|Optionales Attribut. Kann einen oder mehrere der folgenden Werte enthalten:<br /><br /> -   **WarnAndContinue** oder **true**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element [Ziel](../msbuild/target-element-msbuild.md) und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Warnungen behandelt.<br />-   **ErrorAndContinue**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element `Target` und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Fehler behandelt.<br />-   **ErrorAndStop** oder **false** (Standard). Wenn eine Aufgabe fehlschlägt, werden die übrigen Aufgaben im Element `Target` und im Build nicht ausgeführt, und das komplette Element `Target` sowie der Build wird als fehlgeschlagen betrachtet.<br /><br /> Versionen von .NET Framework vor 4.5 unterstützten nur die Werte `true` und `false`.<br /><br /> Weitere Informationen finden Sie unter [Gewusst wie: Ignorieren von Fehlern in Aufgaben](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Erforderlich, wenn die Aufgabenklasse eine oder mehrere Eigenschaften enthält, die mit dem `[Required]`-Attribut gekennzeichnet sind.<br /><br /> Ein benutzerdefinierter Aufgabenparameter, der den Parameterwert als Wert enthält. Das `Task`-Element kann eine beliebige Anzahl von Parametern enthalten, wobei jedes Attribut einer .NET-Eigenschaft in der Aufgabenklasse zugeordnet ist.|  

### <a name="child-elements"></a>Untergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[Ausgabe](../msbuild/output-element-msbuild.md)|Speichert die Ausgaben der Aufgabe in der Projektdatei. Die Aufgabe kann keine oder mehrere `Output`-Elemente enthalten.|  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[Target](../msbuild/target-element-msbuild.md)|Containerelement für [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Aufgaben.|  

## <a name="remarks"></a>Hinweise  
 Ein `Task`-Element in einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projektdatei erstellt eine Instanz einer Aufgabe, legt entsprechende Eigenschaften fest und führt sie aus. Das `Output`-Element speichert Ausgabeparameter in Eigenschaften oder Elementen, damit sie an anderer Stelle in der Projektdatei verwendet werden können.  

 Auch bei [OnError](../msbuild/onerror-element-msbuild.md)-Elementen im übergeordneten `Target`-Element einer Aufgabe werden sie ausgewertet, wenn die Aufgabe fehlschlägt und `ContinueOnError` den Wert `false` aufweist. Weitere Informationen zu Aufgaben finden Sie unter [Aufgaben](../msbuild/msbuild-tasks.md).  

## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel erstellt eine Instanz der [Csc-Aufgabenklasse](../msbuild/csc-task.md), legt sechs Eigenschaften fest und führt die Aufgabe aus. Nach der Ausführung wird der Wert der `OutputAssembly`-Eigenschaft des Objekts in eine Liste mit dem Namen `FinalAssemblyName` aufgenommen.  

```xml  
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

## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Referenz zum MSBuild-Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
