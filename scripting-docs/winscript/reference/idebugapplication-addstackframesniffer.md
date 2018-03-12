---
title: IDebugApplication::AddStackFrameSniffer | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.AddStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::AddStackFrameSniffer
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89faa6481bd5e5934ae2d3b85a0bade83949633a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationaddstackframesniffer"></a>IDebugApplication::AddStackFrameSniffer
Diese Anwendung hinzugefügt einen Stapel Frame Enumerator Anbieter.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdsfs`  
 [in] Der Stapel Frame Enumerator Anbieter dieser Anwendung hinzufügen.  
  
 `pdwCookie`  
 [out] Ein Cookie, mit dem dieser Stapel Frame Enumerator Anbieter aus der Anwendung zu entfernen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Obwohl Sprache-Module in der Regel über diese Methode, um ihre Stapelrahmen an den Debugger verfügbar zu machen aufrufen, ist es möglich, für andere Entitäten Stapelrahmen verfügbar zu machen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)   
 [IDebugStackFrameSniffer-Schnittstelle](../../winscript/reference/idebugstackframesniffer-interface.md)