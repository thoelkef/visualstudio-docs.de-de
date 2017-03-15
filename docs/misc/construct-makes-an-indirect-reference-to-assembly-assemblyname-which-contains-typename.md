---
title: "Konstrukt verweist indirekt auf die Assembly &quot;&lt;Assemblyname&gt;&quot;, die &quot;&lt;Typname&gt;&quot; enth&#228;lt | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31528"
  - "vbc31528"
helpviewer_keywords: 
  - "BC31528"
ms.assetid: 33459c3f-8615-492e-b6ae-531ed597999e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Konstrukt verweist indirekt auf die Assembly &quot;&lt;Assemblyname&gt;&quot;, die &quot;&lt;Typname&gt;&quot; enth&#228;lt
Das Konstrukt verweist indirekt auf die Assembly "\<Assemblyname\>", die "\<Typname\>" enthält. Fügen Sie dem Projekt einen Dateiverweis auf "\<Dateiname\>" hinzu.  
  
 Ein Ausdruck verwendet einen Typ, z. B. eine Klasse, Struktur, Schnittstelle, Enumeration oder einen Delegaten, aber die Assembly enthält keinen Projektverweis auf die Assembly, die den Typ definiert.  
  
 **Fehler\-ID:** BC31528  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie in den Projekteigenschaften einen Verweis auf die Datei mit der Assembly hinzu, die den von Ihnen verwendeten Typ definiert.  
  
## Siehe auch  
 [NOTINBUILD: Auflösen eines Verweises bei mehreren Variablen mit gleichem Namen](http://msdn.microsoft.com/de-de/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB: Gewusst wie: Ändern von Projekteigenschaften und Konfigurationseinstellungen](http://msdn.microsoft.com/de-de/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds "Verweis hinzufügen"](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)