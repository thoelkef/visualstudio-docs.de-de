---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: e5fc3ab0767a7077860c82acefc9554ba1228cee
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831119"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Erlaubt das automatische Anhängen, für die angegebenen Debug-Engines.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
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