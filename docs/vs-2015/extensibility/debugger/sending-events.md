---
title: Senden von Ereignissen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 65c86cb8028d5c310de6f48c753d862865ea7a46
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522260"
---
# <a name="sending-events"></a>Sendeereignisse
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Senden von Ereignissen](https://docs.microsoft.com/visualstudio/extensibility/debugger/sending-events).  
  
Der Mechanismus für die Kommunikation zwischen dem Debugger und die Debug-Engine (DE) ist eine auf DCOM basierende Ereignismodell. Ereignisse werden als COM-Objekte gesendet, und jedes Ereignis verfügt über Parameter, die Folgendes angeben:  
  
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
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Beschreibt die Funktionsweise von einer bereitgestellten Kompatibilitätsrichtlinie mit den Interpreter Betriebssystem oder Debugdienste bereit.

