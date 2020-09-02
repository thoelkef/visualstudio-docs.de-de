---
title: Senden von Ereignissen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98247b894d2db628d508713875ba0ea7d0642729
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204740"
---
# <a name="sending-events"></a>Sendeereignisse
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der Mechanismus für die Kommunikation zwischen dem Debugger und der Debug-Engine (de) ist ein Ereignis Modell, das auf DCOM basiert. Ereignisse werden als COM-Objekte gesendet, und jedes Ereignis verfügt über Parameter, die Folgendes angeben:  
  
- Der de-Wert, der das Ereignis aufgerufen hat.  
  
- Eine Beschreibung, was passiert ist.  
  
- Der Prozess, das Programm und die Thread Informationen, die den Kontext identifizieren, in dem das Ereignis aufgetreten ist. Der Prozess wird nicht für Ereignisse gesendet, die von einem de gesendet werden.  
  
- Der Ereignistyp, der angibt, ob das Ereignis synchron oder asynchron ist.  
  
  Alle Debugereignisse werden mithilfe der [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)-Methode gesendet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Ereignis Quellen](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Erläutert die beiden Quellen für Ereignisse: Debug Engine (de) und Session Debug Manager (SDM).  
  
 [Unterstützte Ereignistypen](../../extensibility/debugger/supported-event-types.md)  
 Erläutert die derzeit unterstützten Ereignis Typen: asynchron und synchron.  
  
 [Ereignisbeschreibungen](../../extensibility/debugger/event-descriptions.md)  
 Definiert Ereignisse und die Gründe für deren Verwendung.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Beschreibt, wie ein de mit dem Interpreter oder dem Betriebssystem verwendet wird, um Debugdienste bereitzustellen.
