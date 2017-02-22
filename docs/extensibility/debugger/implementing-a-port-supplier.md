---
title: "Implementieren einen Port Lieferanten | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK], Port Lieferanten implementieren"
  - "Port-Lieferanten, implementieren"
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementieren einen Port Lieferanten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Stellt anschlüsse des Anschlusslieferanten Debuggen auf Anforderung zum Manager der Sitzung \(SDM\).  Ein Port lieferant während des Debuggens muss implementiert werden oder DCOM nicht auf einen Computer, wenn ein neues Gerät unterstützt werden muss.  Um beispielsweise den Debugvorgang zu einem Mobiltelefon bereitzustellen, implementierten Sie möglicherweise einen Anschlusslieferanten, die Anschlüsse, die an das Mobiltelefon herstellen \(möglicherweise Zellen\-Verbindung\) oder IR mit einer bereitstellt und Prozesse und Programme auflistet, die am Telefon ausgeführt werden.  
  
 Bei Windows\-basierten Computern für Debugprogramme \(einschließlich Remotedebuggen\) stellt Visual Studio Anschlusslieferanten für systemeigen und Prozesse der Common Language Runtime \(CLR\) aufgerufen, sodass keine Anforderung zu implementieren, Anschlusslieferanten in diesen Fällen verfügen.  
  
## In diesem Abschnitt  
 [Implementieren und registrieren einen Port Lieferanten](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Erläutert, wie das SDM für den Anschlusslieferanten und die Ports interagiert.  
  
 [Erforderliche Ports Zulieferer Schnittstellen](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Dokumentiert die Schnittstellen, die implementiert werden müssen, damit ein Anschluss lieferant.  
  
## Verwandte Abschnitte  
 [Debugger\-Konzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die Architektur wichtigsten Konzepte des Debuggens.  
  
## Siehe auch  
 [Visual Studio\-Debugger\-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)