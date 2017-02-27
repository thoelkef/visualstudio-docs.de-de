---
title: "OnError Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#OnError"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "OnError Element [MSBuild]"
  - "<OnError Element [MSBuild]"
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# OnError Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bewirkt, dass ein oder mehrere Ziele ausgeführt werden, wenn das `ContinueOnError`\-Attribut für eine fehlgeschlagene Aufgabe den Wert `false` aufweist.  
  
## Syntax  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung.  Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Erforderliches Attribut.<br /><br /> Die Ziele, die ausgeführt werden sollen, wenn eine Aufgabe fehlschlägt.  Trennen Sie mehrere Ziele durch Semikolons voneinander.  Mehrere Ziele werden in der angegeben Reihenfolge ausgeführt.|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[Target](../msbuild/target-element-msbuild.md)|Containerelement für [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Aufgaben.|  
  
## Hinweise  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] führt das `OnError`\-Element aus, wenn eine der Aufgaben `Target`\-Elements mit dem \- Attribut `ContinueOnError` fehlschlägt, das zu `ErrorAndStop` festgelegt wird \(oder zu `false`\).  Wenn die Aufgabe fehlschlägt, werden die im `ExecuteTargets`\-Attribut angegebenen Ziele ausgeführt.  Enthält das Ziel mehrere `OnError`\-Elemente, werden die `OnError`\-Elemente sequenziell ausgeführt, wenn die Aufgabe fehlschlägt.  
  
 Informationen zum `ContinueOnError`\-Attribut, finden Sie unter [Task Element \(MSBuild\)](../msbuild/task-element-msbuild.md).  Weitere Informationen zu Zielen, finden Sie unter [Targets](../msbuild/msbuild-targets.md).  
  
## Beispiel  
 Mit dem folgenden Code werden die `TaskOne`\-Aufgabe und die `TaskTwo`\-Aufgabe ausgeführt.  Wenn `TaskOne` fehlschlägt, wertet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] das `OnError`\-Element aus und führt das `OtherTarget`\-Ziel aus.  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## Siehe auch  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Targets](../msbuild/msbuild-targets.md)