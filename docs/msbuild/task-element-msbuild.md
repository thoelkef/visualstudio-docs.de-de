---
title: "Task Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "Task element [MSBuild]"
  - "<Task> element [MSBuild]"
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Task Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erstellt eine Instanz einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Aufgabe und führt diese aus.  Der Elementname wird durch den Namen der Aufgabe bestimmt, die erstellt wird.  
  
## Syntax  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Condition`|Optionales Attribut.  Die auszuwertende Bedingung.  Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Optionales Attribut.  Kann einen der folgenden Werte enthalten:<br /><br /> -   **WarnAndContinue** oder **true**.  Wenn eine Aufgabe fehlschlägt, werden folgende Aufgaben im [Ziel](../msbuild/target-element-msbuild.md)\-Element und im Build fort, um auszuführen, und alle Fehler von der Aufgabe werden als Warnungen behandelt.<br />-   **ErrorAndContinue**.  Wenn eine Aufgabe fehlschlägt, werden folgende Aufgaben im `Target`\-Element und im Build fort, um auszuführen, und alle Fehler von der Aufgabe werden als Fehler behandelt.<br />-   **ErrorAndStop** oder **false** \(Standard\).  Wenn eine Aufgabe fehlschlägt, werden die übrigen Aufgaben im `Target`\-Element und im Build nicht ausgeführt, und das gesamte `Target`\-Element und der Build wird angenommen fehlgeschlagen sein.<br /><br /> .NET Framework\-Versionen vor 4,5 unterstützten nur die `true` und `false`\-Werte.<br /><br /> Weitere Informationen finden Sie unter [How to: Ignore Errors in Tasks](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Erforderlich, wenn die Aufgabenklasse eine oder mehrere Eigenschaften mit dem `[Required]`\-Attribut enthält.<br /><br /> Ein benutzerdefinierter Aufgabenparameter, dessen Wert dem Parameterwert entspricht.  Das `Task`\-Element kann beliebig viele Parameter enthalten, wobei jedes Attribute einer .NET\-Eigenschaft in der Aufgabenklasse zugeordnet wird.|  
  
### Untergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[Ausgabe](../msbuild/output-element-msbuild.md)|Speichert die Ausgaben der Aufgabe in der Projektdatei.  Es kann keine oder mehrere `Output`\-Elemente in einer Aufgabe geben.|  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[Target](../msbuild/target-element-msbuild.md)|Containerelement für [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Aufgaben.|  
  
## Hinweise  
 Ein `Task`\-Element in einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projektdatei erstellt eine Instanz einer Aufgabe, legt entsprechende Eigenschaften fest und führt die Aufgabe aus.  Das `Output`\-Element speichert Ausgabeparameter in Eigenschaften oder Elementen, die an anderer Stelle in der Projektdatei verwendet werden sollen.  
  
 Wenn das übergeordnete `Target`\-Element einer Aufgabe [OnError](../msbuild/onerror-element-msbuild.md)\-Elemente enthält, werden diese auch ausgewertet, falls die Aufgabe fehlschlägt und `ContinueOnError` den Wert `false` aufweist.  Weitere Informationen zu Aufgaben finden Sie unter [Tasks](../msbuild/msbuild-tasks.md).  
  
## Beispiel  
 Im folgenden Codebeispiel wird eine Instanz der [Csc task](../msbuild/csc-task.md)\-Aufgabe erstellt, dann werden sechs Eigenschaften festgelegt, und die Aufgabe wird ausgeführt.  Nach der Ausführung wird der Wert der `OutputAssembly`\-Eigenschaft des Objekts in eine Elementliste mit dem Namen `FinalAssemblyName` eingefügt.  
  
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
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)