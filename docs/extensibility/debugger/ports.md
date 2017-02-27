---
title: "Ports | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Anschlüsse"
  - "Debuggen [Debugging-SDK]-ports"
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Ports
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Hinblick auf die Architektur der Debugger ein **Anschluss**:  
  
-   Ist ein Container für eine Gruppe von Prozessen, die auf einem Server ausgeführt werden.  Beispielsweise kann ein Port eine Verbindung zu einem CE\-basierten Gerät Fenster durch ein serielles Verbindung oder einem vernetzten Computer Nicht DCOM dar.  Ein spezieller Port bezeichnet den lokalen Anschluss enthält alle Prozesse, die auf dem lokalen Computer ausgeführt werden.  
  
-   Kann sich über den Namen oder Bezeichner identifiziert.  
  
-   Alle Prozesse auflisten kann das Ausführen auf den angegebenen Anschluss und starten und diese Prozesse beenden.  
  
-   Wird von einer [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)\-Schnittstelle dargestellt, die erstellt wird, indem ein [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)\-Argument an [Port hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)übergeben wird.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Stellt ein Standardanschluss, der alle Windows\-basierten Prozesse verarbeitet, systemeigenen und verwalteten.  Ein benutzerdefinierter Port muss für Verbindungen mit externen Geräten, die keine Implementierung Windows\-basiert sind.  Um solche benutzerdefinierten Ports einen benutzerdefinierten Port angeben, muss auch lieferant implementiert werden.  
  
## Siehe auch  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Debugger\-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Port hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)