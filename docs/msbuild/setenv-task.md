---
title: "SetEnv Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.setenv"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), tasks"
  - "SetEnv task (MSBuild (Visual C++))"
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# SetEnv Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Legt den Wert einer angegebenen Umgebungsvariablen fest oder löscht ihn.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der **SetEnv** \-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|**Name**|Erforderlicher **String**\-Parameter.<br /><br /> Der Name einer Umgebungsvariablen.|  
|**OutputEnvironmentVariable**|Optionaler **String**\-Ausgabeparameter.<br /><br /> Enthält den Wert, der der Umgebungsvariable zugewiesen ist, die vom **Name**\-Parameter angegeben wird.|  
|**Prefix**|Verbindlicher `Boolean`\-Parameter<br /><br /> Wenn `true`, wird der Wert des **Value**\-Parameters vor dem Wert der Umgebungsvariable verkettet, die vom **Name**\-Parameter angegeben wird, und anschließend wird das Ergebnis der Umgebungsvariable zugewiesen.  Wenn `false`, wird der Umgebungsvariable nur der Wert des **Value**\-Parameters zugewiesen.|  
|**Target**|Optionaler **String**\-Parameter.<br /><br /> Gibt den Speicherort an, an dem eine Umgebungsvariable gespeichert wird.  Geben Sie `Benutzer` oder `Computer` an.<br /><br /> Weitere Informationen finden Sie unter "EnvironmentVariableTarget\-Enumeration" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**Value**|Optionaler **String**\-Parameter.<br /><br /> Der Wert, der der Umgebungsvariable zugewiesen ist, die vom **Name**\-Parameter angegeben wird.  Wenn **Value** leer ist und die Variable vorhanden ist, wird die Umgebungsvariable gelöscht.  Wenn die Variable nicht vorhanden ist, tritt kein Fehler auf, obwohl die Operation nicht ausgeführt werden kann.<br /><br /> Weitere Informationen finden Sie unter "Environment::SetEnvironmentVariable\-Methode" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
  
## Hinweise  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)