---
title: 'Idebugdocumenthelper:: Adddbcstext | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDBCSText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDBCSText
ms.assetid: 5e5011b2-bbb4-491b-9a11-eb2846be44aa
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d346f3877574c45aaff6dcef8ca99f699a42552
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446654"
---
# <a name="idebugdocumenthelperadddbcstext"></a>IDebugDocumentHelper::AddDBCSText
Fügt eine DBCS-Zeichenfolge am Ende dieses Dokuments.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddDBCSText(  
   LPCSTR  pszText  
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
> Wenn diese Methode, nach dem aufgerufen wird `IDebugDocumentHelper::AddDeferredText` aufgerufen wurde, `E_FAIL` zurückgegeben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [IDebugDocumentTextEvents-Schnittstelle](../../winscript/reference/idebugdocumenttextevents-interface.md)