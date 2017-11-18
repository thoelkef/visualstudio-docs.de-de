---
title: IDebugApplication110-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd7c283e925db5b42b4d04bfc42ea087ecc22b6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication110-interface"></a>IDebugApplication110-Schnittstelle
Die `IDebugApplication110` -Schnittstelle erweitert die Funktionalität der [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md). Sie erhalten eine Instanz dieser Schnittstelle durch den Aufruf von QueryInterface bei der Implementierung der [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IDebugApplication110`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Stellt einen synchronen Aufruf im Hauptthread an.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Stellt einen asynchronen Aufruf im Hauptthread an.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Wartet, bis eines der angegebenen Handles signalisiert wird, während gleichzeitig threadübergreifende Aufrufe an diesen Thread bereitgestellt werden. Diese Methode muss von dem Debuggerthread aufgerufen werden.|