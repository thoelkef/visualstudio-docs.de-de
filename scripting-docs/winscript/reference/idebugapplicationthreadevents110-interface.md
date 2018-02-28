---
title: IDebugApplicationThreadEvents110-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aaf312b1730696b812172aeea175619e911d03a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110-Schnittstelle
Fügt Weitere Threadereignisse hinzu. Diese Ereignisse sind nur lokal. Also können Sie abonnieren sie nur in dem Prozess zu debuggen, indem Sie die [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) anmelden und Methoden auf PDM Anwendung Threadobjekte (Objekte implementiert, [IDebugApplicationThread Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md)). Die Zeitpunkte für den Thread, der von kommen.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IDebugActivationThreadEvents110`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Ein Aufruf in dem Thread, der mithilfe der PDM Threads wechseln begonnen hat.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Der Thread wird von einem Haltepunkt fortgesetzt und erneut aktiv sein wird.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Der Thread wird aktuell für einen Haltepunkt angehalten und Aufrufe, die den Thread vollständig anzuhaltende erfordern verarbeiten kann.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Ein Aufruf in dem Thread, der mithilfe der PDM Threads wechseln abgeschlossen wurde.|