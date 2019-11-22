---
title: IDebugApplicationThreadEvents110-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5dd666d825c40155675714f5945209f22198993c
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984395"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110-Schnittstelle
Fügt weitere Thread Ereignisse hinzu. Diese Ereignisse sind nur lokal. Das heißt, Sie können Sie nur im debuggten Prozess abonnieren. verwenden Sie dazu die [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) -Methoden "Empfehlung" und "unempfehlung" für PDM-Anwendungs Thread Objekte (Objekte, die die [idebugapplicationthread-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md)implementieren). Sie treten auf dem Thread auf, von dem Sie stammen.  
  
> [!IMPORTANT]
> Diese Schnittstelle wird von PDM v11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IDebugActivationThreadEvents110`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Ein Rückruf für den Thread, der den PDM-Thread Wechsel verwendet, wurde begonnen.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Der Thread wird von einem Breakpoint fortgesetzt und wird wieder aktiviert.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Der Thread wird für einen Haltepunkt angehalten und kann Aufrufe verarbeiten, die erfordern, dass der Thread vollständig angehalten wird.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Ein Rückruf für den Thread, der den PDM-Thread Wechsel verwendet, wurde abgeschlossen.|