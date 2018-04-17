---
title: Senden von Ereignissen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9bbe7946b866cd751be1f0dac2dba5b8dea57e04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sending-events"></a>Senden von Ereignissen
Der Mechanismus für die Kommunikation zwischen dem Debugger und die Debugging-Modul (DE) ist ein Ereignismodell, basierend auf DCOM. Ereignisse werden als COM-Objekte gesendet, und jedes Ereignis verfügt über Parameter, die Folgendes angeben:  
  
-   Die DE, die das Ereignis aufgerufen wird.  
  
-   Eine Beschreibung der Ursache.  
  
-   Der Prozess, Programm- und Threadinformationen, der Kontext identifiziert, in dem das Ereignis aufgetreten ist. Der Prozess wird nicht für Ereignisse, die aus einer bereitgestellten Kompatibilitätsrichtlinie gesendet gesendet.  
  
-   Der Ereignistyp, der angibt, ob das Ereignis synchron oder asynchron ist.  
  
 Alle Debug-Ereignisse gesendet werden, mithilfe der Methode [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Ereignisquellen](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Erläutert die zwei Quellen von Ereignissen: Debuggen von Debugging-Modul (Deutschland) und die Sitzung Manager (SDM).  
  
 [Unterstützte Ereignistypen](../../extensibility/debugger/supported-event-types.md)  
 Erläutert, die derzeit unterstützten Ereignistypen: asynchrone und synchrone.  
  
 [Ereignisbeschreibungen](../../extensibility/debugger/event-descriptions.md)  
 Definiert, Ereignisse und die Gründe für deren Verwendung.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Beschreibt die Funktionsweise von einer bereitgestellten Kompatibilitätsrichtlinie mit den Interpreter Betriebssystem oder Debugdienste bereit.