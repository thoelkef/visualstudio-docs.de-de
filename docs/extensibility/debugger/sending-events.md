---
title: Senden von Ereignissen | Microsoft-Dokumentation
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
ms.openlocfilehash: 87087a2087591b01170b82c0335e4bbffc579cc2
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252452"
---
# <a name="send-events"></a>Senden von Ereignissen
Der Mechanismus für die Kommunikation zwischen dem Debugger und die Debug-Engine (DE) ist eine auf DCOM basierende Ereignismodell. Ereignisse werden als COM-Objekte gesendet, und jedes Ereignis verfügt über Parameter, die angeben:  
  
-   Die DE, die das Ereignis aufgerufen.  
  
-   Eine Beschreibung des was passiert ist.  
  
-   Der Prozess, Anwendung und Threadinformationen, identifiziert der Kontext, in dem das Ereignis aufgetreten ist. Der Prozess wird nicht für Ereignisse, die von einer bereitgestellten Kompatibilitätsrichtlinie gesendeten gesendet.  
  
-   Der Ereignistyp, der angibt, ob das Ereignis synchron oder asynchron ist.  
  
 Alle Debug-Ereignisse gesendet werden, mithilfe der Methode [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Ereignisquellen](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Erläutert, die zwei Quellen von Ereignissen: die Debug-Engine (DE) und die Sitzung debug-Manager (SDM).  
  
 [Unterstützte Ereignistypen](../../extensibility/debugger/supported-event-types.md)  
 Erläutert, die derzeit unterstützten Ereignistypen: asynchrone und synchrone.  
  
 [Ereignisbeschreibungen](../../extensibility/debugger/event-descriptions.md)  
 Definiert Ereignisse und die Gründe für deren Verwendung.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen einer benutzerdefinierten Debug-engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Beschreibt die Funktionsweise von einer bereitgestellten Kompatibilitätsrichtlinie mit den Interpreter Betriebssystem oder Debugdienste bereit.