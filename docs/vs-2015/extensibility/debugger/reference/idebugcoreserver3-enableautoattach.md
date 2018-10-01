---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4b5c420a03fd69d767331f356eb4353d52630376
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514882"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugCoreServer3::EnableAutoAttach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcoreserver3-enableautoattach).  
  
Erlaubt das automatische Anhängen, für die angegebenen Debug-Engines.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

