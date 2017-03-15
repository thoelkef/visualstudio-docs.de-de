---
title: "Es ist ein Verweis auf die Assembly &quot;&lt;Assemblyidentit&#228;t&gt;&quot; erforderlich, die den Typ &quot;&lt;Typname&gt;&quot; enth&#228;lt, aber aufgrund m&#246;glicher Zirkelverweise wurde kein geeigneter Verweis gefunden: &lt;Verweisabh&#228;ngigkeitsliste&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30962"
  - "vbc30962"
helpviewer_keywords: 
  - "BC30962"
ms.assetid: 6f338158-bfb4-4cc0-bbf7-1111c708613c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es ist ein Verweis auf die Assembly &quot;&lt;Assemblyidentit&#228;t&gt;&quot; erforderlich, die den Typ &quot;&lt;Typname&gt;&quot; enth&#228;lt, aber aufgrund m&#246;glicher Zirkelverweise wurde kein geeigneter Verweis gefunden: &lt;Verweisabh&#228;ngigkeitsliste&gt;
Ein Ausdruck verwendet einen Typ \(z. B. eine Klasse, eine Struktur, eine Schnittstelle, eine Enumeration oder einen Delegaten\), der außerhalb des Projekts definiert ist. Der Projektverweis auf diese Assembly ist jedoch Teil einer Gruppe von Zirkelverweisen.  
  
 Wenn mehrere Projekte aufeinander verweisen, können die Verweise *zirkulär* sein. So können beispielsweise zwei Projekte jeweils einen Verweis auf das andere Projekt enthalten. Allgemeiner ausgedrückt kann eine Kette von Verweisen von einem Projekt auf das nächste letztendlich wieder zum Ausgangsprojekt zurückführen. In solchen Fällen fehlt ein endgültiges Projekt am Ende der Kette, mithilfe dessen der Verweis aufgelöst werden kann.  
  
 Für den Zugriff auf einen Typ, der in einer anderen Assembly definiert ist, benötigt der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler einen Verweis auf diese Assembly. Dabei muss es sich um einen einzelnen, eindeutigen Verweis handeln, der keine Zirkelverweise in Projekten verursacht.  
  
 **Fehler\-ID:** BC30962  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie in den Projekteigenschaften einen direkten Verweis auf das Projekt hinzu, aus dem die Assembly erzeugt wird, die den von Ihnen verwendeten Typ definiert.  
  
## Siehe auch  
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [NIB: Verweisen auf Namespaces und Komponenten](http://msdn.microsoft.com/de-de/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds "Verweis hinzufügen"](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB: Gewusst wie: Ändern von Projekteigenschaften und Konfigurationseinstellungen](http://msdn.microsoft.com/de-de/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)