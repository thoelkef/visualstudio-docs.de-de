---
title: "ResolveKeySource Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ResolveKeySource task [MSBuild]"
  - "MSBuild, ResolveKeySource task"
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# ResolveKeySource Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ermittelt die Quelle für Schlüssel für einen starken Namen.  
  
## Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `ResolveKeySource`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`AutoClosePasswordPromptShow`|Optionaler `Int32`\-Parameter.<br /><br /> Ruft die Zeitspanne \(in Sekunden\) für die Anzeige der Countdownmeldung ab oder legt diese fest.|  
|`AutoClosePasswordPromptTimeout`|Optionaler `Int32`\-Parameter.<br /><br /> Ruft die Zeitspanne \(in Sekunden\) ab, die bis zum Schließen des Dialogfelds mit der Kennworteingabeaufforderung gewartet werden soll, oder legt diese fest.|  
|`CertificateFile`|Optionaler `String`\-Parameter.<br /><br /> Ruft den Pfad der Zertifikatsdatei ab oder legt ihn fest.|  
|`CertificateThumbprint`|Optionaler `String`\-Parameter.<br /><br /> Ruft den Fingerabdruck des Zertifikats ab oder legt ihn fest.|  
|`KeyFile`|Optionaler `String`\-Parameter.<br /><br /> Ruft den Pfad der Schlüsseldatei ab oder legt ihn fest.|  
|`ResolvedKeyContainer`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Ruft den Container für aufgelöste Schlüssel ab oder legt diesen fest.|  
|`ResolvedKeyFile`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Ruft die aufgelöste Schlüsseldatei ab oder legt diese fest.|  
|`ResolvedThumbprint`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Ruft den Fingerabdruck des aufgelösten Zertifikats ab oder legt ihn fest.|  
|`ShowImportDialogDespitePreviousFailures`|Optionaler `Boolean`\-Parameter.<br /><br /> Bei `true` wird das Importdialogfeld trotz vorheriger Fehler angezeigt.|  
|`SuppressAutoClosePasswordPrompt`|Optionaler `Boolean`\-Parameter.<br /><br /> Ruft einen booleschen Wert ab, der angibt, ob das Dialogfeld mit der Kennworteingabeaufforderung automatisch geschlossen werden soll, oder legt diesen fest.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)