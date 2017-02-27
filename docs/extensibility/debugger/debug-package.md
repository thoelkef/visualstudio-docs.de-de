---
title: "Debug-Paket | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK] Pakete"
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Debug-Paket
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Debuggen von in die Visual Studio\-Shell Paket ausgeführt wird, und behandelt alle Benutzeroberfläche.  Es nutzt die Visual Studio\-Debugschnittstellen den Debug\- und die Kommunikation mit der Sitzung Manager \(SDM\).  
  
 Unterteilen Sie die Ereignisse, die vom SDM gesendet werden, den Debugger von Ausführmodus zu wechseln und Unterbrechungsmodus bearbeiten den Fokus auf das Programm, in dem die Unterbrechung aufgetreten ist.  Das Debuggen von Paket verfolgt den Stapelrahmen und den Thread aus den Informationen, die von den Ereignissen gesendet werden.  
  
 Das Debuggen von Paket enthält keine Momentaufnahme für die Sprach\- oder von Abhängigkeiten.  Es ist nicht notwendig, das Debuggen Paket zu implementieren oder zu ändern.  
  
 Das Debuggen von Paket wird vsdebug.dll implementiert.  
  
## Siehe auch  
 [Session\-Debug\-Manager](../../extensibility/debugger/session-debug-manager.md)   
 [Stapelrahmen](../../extensibility/debugger/stack-frames.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)