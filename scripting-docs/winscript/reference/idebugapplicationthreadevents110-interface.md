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
ms.openlocfilehash: 0051f18c67fffc9801ad326745a0dc9dd63f4391
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148853"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110-Schnittstelle
Weitere Threadereignisse hinzugefügt. Diese Ereignisse sind nur lokal. D. h. Sie abonniert werden können nur in dem Prozess zu debuggen, indem die [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) anmelden und Methoden auf PDM-Application-Thread-Objekte (Objekte, die implementieren [IDebugApplicationThread Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md)). Sie werden auf dem Thread aus, von dem sie stammen.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IDebugActivationThreadEvents110`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Ein Aufruf in dem Thread, der über das PDM Thread gewechselt wurde gestartet.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Der Thread wird von einem Haltepunkt fortgesetzt, und es wird wieder aktiv sein.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Der Thread für einen Haltepunkt angehalten wird und Aufrufe, die den Thread vollständig unterbrochen wird, erfordern verarbeiten kann.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Ein Aufruf in dem Thread, der über das PDM Thread gewechselt wurde abgeschlossen.|