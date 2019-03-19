---
title: IDebugApplication110-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c040df103bac464e4f440f23674da966063f0ae
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149668"
---
# <a name="idebugapplication110-interface"></a>IDebugApplication110-Schnittstelle
Die `IDebugApplication110` Schnittstelle erweitert die Funktionalität der [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md). Sie können eine Instanz dieser Schnittstelle abrufen, indem Sie QueryInterface aufrufen, bei der Implementierung der [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IDebugApplication110`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Stellt einen synchronen Aufruf im Hauptthread verarbeitet.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Führt einen asynchronen Aufruf im Hauptthread verarbeitet.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Wartet darauf, eines der angegebenen Handles signalisiert wird, während gleichzeitig threadübergreifende Aufrufe, die für diesen Thread bereitgestellt werden. Diese Methode muss aus dem Debuggerthread aufgerufen werden.|