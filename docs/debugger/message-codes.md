---
title: "Message Codes | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message codes"
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Message Codes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Jede in der [Meldungsansicht](../debugger/messages-view.md) angezeigte Meldungszeile enthält den Code "P", "S", "s" oder "R".  Diese Codes haben folgende Bedeutung:  
  
|Code|Bedeutung|  
|----------|---------------|  
|P|Die Meldung wurde mit der Funktion **PostMessage** in der Warteschlange bereitgestellt.  Es sind keine Informationen über die endgültige Anordnung für die Meldung verfügbar.|  
|S|Die Meldung wurde mit der Funktion **SendMessage** gesendet.  Dies bedeutet, dass die Steuerung erst wieder an den Absender übergeht, wenn der Empfänger die Meldung verarbeitet und zurücksendet.  Daher kann der Empfänger einen Rückgabewert an den Absender übergeben.|  
|s|Die Meldung wurde gesendet, aus Sicherheitsgründen wird jedoch der Zugriff auf den Rückgabewert verhindert.|  
|R|Für jede S\-Zeile ist eine entsprechende R\-Zeile \(Return, Rückgabe\) vorhanden, die den Rückgabewert der Meldung enthält.  Manchmal sind Meldungsaufrufe geschachtelt. Dies bedeutet, dass ein Meldungshandler eine andere Meldung sendet.|