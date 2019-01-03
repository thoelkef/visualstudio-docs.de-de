---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2477ac13218342511ac7b47bec6cf847651cfb22
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913069"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Erlaubt das automatische Anhängen, für die angegebenen Debug-Engines.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `rgguidSpecificEngines`  
 [in] Array von GUIDs für jedes Debugmodul markieren als von der automatischen anfügen.  
  
 `celtSpecificEngines`  
 [in] Die Anzahl der Module, die im angegebenen `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 [in] Die Start-URL zu verwenden, wenn das automatische Anhängen.  
  
 `pbstrSessionID`  
 [out] Die ID der Sitzung, die automatisch angefügt wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls den Fehlercode zurück. Ein Fehlercode `E_AUTO_ATTACH_NOT_REGISTERED`, was bedeutet, dass die Klassenfactory Auto-attach nicht registriert wurde.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Programm verknüpft ist, mit der angegebenen URL gestartet wird, werden die angegebenen Debug-Engines automatisch gestartet und angefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)