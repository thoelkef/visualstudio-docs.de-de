---
title: "Problembehandlung bei Ausnahmen: System.NotSupportedException | Microsoft Docs"
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
  - "NotSupportedException-Klasse"
ms.assetid: a214e851-ee0f-4bbd-9f72-8769046526f3
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.NotSupportedException
Eine <xref:System.NotSupportedException>\-Ausnahme wird ausgelöst, wenn eine aufgerufene Methode nicht unterstützt wird oder wenn versucht wird, lesend, suchend oder schreibend auf einen Stream zuzugreifen, der die aufgerufene Funktionalität nicht unterstützt.  
  
## Tipps  
 **Stellen Sie sicher, dass die Methode unterstützt wird.**  
 Es gibt Methoden, die in der Basisklasse nicht unterstützt werden, und es besteht die Erwartung, dass sie stattdessen in den abgeleiteten Klassen unterstützt werden. Wenn eine abgeleitete Klasse nur einen Teil der Methoden der Basisklasse implementiert, löst sie eine <xref:System.NotSupportedException>\-Ausnahme für die nicht unterstützten Methoden aus.  
  
## Hinweise  
 Wenn Sie mit [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] arbeiten und in einer systemeigenen Funktion P\/Invoke verwenden, können folgende Bedingungen zum Auslösen der Ausnahme führen:  
  
-   Die Deklaration im verwalteten Code ist nicht korrekt.  
  
-   Ihre Aktion wird nicht von [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] unterstützt.  
  
-   Die DLL\-Namen werden beim Export geändert.  
  
-   Prüfen Sie in so einem Fall:  
  
-   Ob Verstöße gegen die P\/Invoke\-Beschränkungen von [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] vorliegen.  
  
-   Ob Argumente vorhanden sind, die im Voraus belegten Arbeitsspeicher erfordern. Falls sie vorhanden sind, sollten Sie einen Verweis auf eine vorhandene Variable übergeben.  
  
-   Ob die Namen der exportierten Funktionen korrekt sind. Dies kann mithilfe von DumpBin.exe überprüft werden.  
  
-   Ob Sie zu viele Argumente zu übergeben versuchen.  
  
## Siehe auch  
 <xref:System.NotSupportedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)