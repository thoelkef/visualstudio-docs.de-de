---
title: "Problembehandlung bei Ausnahmen: System.IO.FileNotFoundException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "FileNotFoundException-Klasse"
  - "System.IO.FileNotFoundException-Ausnahme"
ms.assetid: 6e5ab395-7c81-434e-835f-0fc792b9149d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.IO.FileNotFoundException
Die <xref:System.IO.FileNotFoundException>\-Ausnahme wird bei dem Versuch ausgelöst, auf eine Datei oder ein Verzeichnis zuzugreifen, die bzw. das nicht auf dem Laufwerk vorhanden ist.  
  
## Tipps  
 **Stellen Sie sicher, dass die Datei am angegebenen Speicherort vorhanden ist.**  
 Wenn die Datei nicht vorhanden ist, wird diese Ausnahme ausgelöst. Weitere Informationen finden Sie unter <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A>.  
  
 **Wenn Sie relative Pfade verwenden, müssen Sie überprüfen, ob das aktuelle Verzeichnis korrekt ist.**  
 Wenn von einem falschen Verzeichnis ausgegangen wird, sind die relativen Pfade ebenfalls falsch.  
  
## Siehe auch  
 <xref:System.IO.FileNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)