---
title: 'IDebugApplicationThread110:: getactivethreadrequestcount | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7f038c1d0958701a14899825a2adb0a11cf604d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574481"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Gibt die Anzahl der Thread Anforderungen aus den Thread Wechsel Mechanismen des PDM zurück, die gerade verarbeitet werden. Diese Zahl ist normalerweise 0 (null) oder 1. Die Zahl kann jedoch höher sein, wenn ein Thread Aufruf die Verarbeitung startet, aber einen synchronen Aufruf aus dem Thread auslöst oder andernfalls den Thread anhält und zulässt, dass eingehende Aufrufe erneut verarbeitet werden (z. b. durch Auslösen eines [iremotedebugapplicationevents). Ein Schnittstellen](../../winscript/reference/iremotedebugapplicationevents-interface.md) Ereignis, das im Debugger-Thread ausgegeben wird.  
  
> [!IMPORTANT]
> Die [IDebugApplicationThread110-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parameter  
 `puiThreadRequests`  
 vorgenommen Die Anzahl der Thread Anforderungen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationThread110-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md)