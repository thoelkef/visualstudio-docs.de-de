---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords: IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d0b7fbfc1d7c3d9d4ab5214e8c0c5518c6dad5cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Ermöglicht das automatische anfügen für die angegebene Debug-Module.  
  
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
 [in] Die Start-URL zu verwendende automatische anfügen.  
  
 `pbstrSessionID`  
 [out] Die ID der Sitzung, die automatisch angefügt wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`; andernfalls wird Fehlercode zurückgegeben. Wird ein Fehlercode `E_AUTO_ATTACH_NOT_REGISTERED`, was bedeutet, dass die Klassenfactory Auto-attach nicht registriert wurde.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Programm, das der angegebenen URL zugeordnete gestartet wird, werden die angegebenen Debugmodule automatisch gestartet und angefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)