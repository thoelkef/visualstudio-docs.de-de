---
title: 'Ijsdebugframe:: Evaluation-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6227b97c1fd5fae32db3e13ef72751726c36b043
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573499"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate-Methode
Werten Sie einen Ausdruck im Kontext dieses Stapelrahmens aus.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pExpressionText`  
 [in] Der auszuwertende Ausdruck.  
  
 `ppDebugProperty`  
 [out] Objekt, das den Eigenschaftenbrowser darstellt.  
  
 `pError`  
 [out] Die Fehlermeldung, wenn ein Fehler auftritt.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Gibt Folgendes zurück: "S_OK": Auswertung folgt, "*ppDebugProperty" enthält Auswertungsergebnis. S_FALSE: die Auswertung löst einen Fehler aus (oder der Auswertungs Vorgang wird nicht unterstützt), \*pError die die Fehlermeldung enthält.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugFrame-Schnittstelle](../../winscript/reference/ijsdebugframe-interface.md)