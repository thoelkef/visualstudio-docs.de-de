---
title: IDebugApplication110-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b13208d6a507ea4ed3157606f358b6b0168180cf
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349555"
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