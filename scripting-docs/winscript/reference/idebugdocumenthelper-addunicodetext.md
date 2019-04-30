---
title: 'Idebugdocumenthelper:: Addunicodetext | Microsoft-Dokumentation'
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
ms.openlocfilehash: 391095acc1d2f541a3c497abeac5ae7248baa4e8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446626"
---
# <a name="idebugdocumenthelperaddunicodetext"></a>IDebugDocumentHelper::AddUnicodeText
Fügt eine Unicode-Zeichenfolge am Ende dieses Dokuments.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddUnicodeText(  
   LPCOLESTR  pszText  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszText`  
 [in] Zeiger auf eine Null-terminierte Zeichenfolge, die mit dem Text.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die Methode konnte nicht die Zeichen hinzufügen.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode generiert `IDebugDocumentTextEvents` Benachrichtigungen.  
  
> [!NOTE]
> Wenn diese Methode, nach dem aufgerufen wird `AddDeferredText` aufgerufen wurde, `E_FAIL` zurückgegeben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [IDebugDocumentTextEvents-Schnittstelle](../../winscript/reference/idebugdocumenttextevents-interface.md)