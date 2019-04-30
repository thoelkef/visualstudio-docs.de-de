---
title: Adddeferredtext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2f2a7c134142668613cc38cee9357e42cb95096
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433943"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Benachrichtigt, dass der angegebene Text verfügbar ist, aber es nicht die Zeichen bietet der-Hilfe.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cChars`  
 [in] Anzahl der Zeichen (Unicode) hinzufügen.  
  
 `dwTextStartCookie`  
 [in] Host definierten Cookie, das die Anfangsposition des Texts darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Fehler bei der Methode.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermöglicht den Host für das Zurückstellen der Zeichen hinzufügen, bis sie benötigt werden, während gleichzeitig das Hilfsprogramm zum Generieren genau Benachrichtigungen und Informationen zur Größe von. Die `dwTextStartCookie` -Parameter ist ein Cookie, definiert durch den Host, der die Anfangsposition des Texts darstellt. Nachfolgende Aufrufe von `IDebugDocumentText::GetText` müssen dieses Cookie angeben. Beispielsweise konnte in einem Host, der Text in DBCS darstellt, das Cookie ein Byte-Offset werden.  
  
 Es wird davon ausgegangen, dass ein einzelner Aufruf `IDebugDocumentText::GetText` erhalten Zeichen aus mehreren Aufrufen an `AddDeferredText`. Hilfsklassen unter Umständen auch mehrmals für denselben Umfang an verzögerte Zeichen erforderlich.  
  
> [!NOTE]
> Aufrufe von `AddDeferredText` dürfen nicht gemischt werden durch Aufrufe `AddUnicodeText` oder `AddDBCSText`. In diesem Fall `E_FAIL` zurückgegeben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)