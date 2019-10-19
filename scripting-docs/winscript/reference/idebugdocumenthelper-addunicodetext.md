---
title: 'Idebugdocumenthelper:: addunicodetext | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddUnicodeText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddUnicodeText
ms.assetid: f4ef648e-c55d-4ef0-8df3-e808b798d3b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5820c380c92f2c3cd95763b440d5f9755db3e717
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577053"
---
# <a name="idebugdocumenthelperaddunicodetext"></a>IDebugDocumentHelper::AddUnicodeText
Fügt eine Unicode-Zeichenfolge an das Ende dieses Dokuments an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddUnicodeText(  
   LPCOLESTR  pszText  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszText`  
 in Zeiger auf eine mit NULL endenden Zeichenfolge, die den Text enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die-Methode konnte die Zeichen nicht hinzufügen.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode generiert `IDebugDocumentTextEvents` Benachrichtigungen.  
  
> [!NOTE]
> Wenn diese Methode aufgerufen wird, nachdem `AddDeferredText` aufgerufen wurde, wird `E_FAIL` zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugdocumenthelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)    
 [Idebugdocumenthelper:: adddeferredtext](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [IDebugDocumentTextEvents-Schnittstelle](../../winscript/reference/idebugdocumenttextevents-interface.md)