---
title: T4-Textvorlagendirektiven | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1ebe8e7f4872e36fb24987467b76adb6f65d2ed5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="t4-text-template-directives"></a>T4-Textvorlagenanweisungen
Durch Anweisungen werden Anweisungen für das Textvorlagen-Transformationsmodul bereitgestellt.  
  
 Die Syntax von Direktiven lautet wie folgt:  
  
```  
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>  
```  
  
 Alle Attributwerte müssen in doppelte Anführungszeichen eingeschlossen werden. Wenn der Wert selbst Anführungszeichen enthält, müssen diese mit dem Escapezeichen "\" versehen werden.  
  
 Direktiven sind in der Regel die ersten Elemente in einer Vorlagendatei oder einer eingeschlossenen Datei. Platzieren Sie sie nicht in einem Codeblock `<#...#>` und nicht nach einem Klassenfunktionsblock `<#+...#>`.  
  
 [T4-Vorlagenanweisung](../modeling/t4-template-directive.md)  
 ```  
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 [T4-Parameter-Direktive](../modeling/t4-parameter-directive.md)  
 ```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 [T4 Output-Direktive](../modeling/t4-output-directive.md)  
 ```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 [T4-Assemblydirektive](../modeling/t4-assembly-directive.md)  
 ```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 [T4-Import-Anweisung](../modeling/t4-import-directive.md)  
 ```  
<#@ import namespace="namespace" #>  
```  
  
 [T4-Include-Direktive](../modeling/t4-include-directive.md)  
 ```  
<#@ include file="filePath" #>  
```  
  
 [T4 CleanUpBehavior-Anweisung](../modeling/t4-cleanupbehavior-directive.md)  
 ```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Darüber hinaus können Sie eigene Anweisungen erstellen. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten T4 Text Vorlage Direktivenprozessoren](../modeling/creating-custom-t4-text-template-directive-processors.md). Wenn Sie mithilfe des Visualisierungs- und Modellierungs-SDKs eine domänenspezifische Sprache (DSL) erstellen, wird ein Direktivenprozessor als Teil der DSL generiert.