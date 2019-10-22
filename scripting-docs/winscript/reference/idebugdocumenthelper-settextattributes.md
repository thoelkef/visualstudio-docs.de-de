---
title: 'Idebugdocumenthelper:: settextattributes | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetTextAttributes
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetTextAttributes
ms.assetid: 31657738-9e4c-436a-be61-23f4185d452e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cc5e5955652fd8b59d4c502e68d97a729ded141
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569463"
---
# <a name="idebugdocumenthelpersettextattributes"></a>IDebugDocumentHelper::SetTextAttributes
Legt die Attribute für einen Textbereich fest und überschreibt andere Attribute für diesen Text.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetTextAttributes(  
   ULONG              ulCharOffset,  
   ULONG              cChars,  
   SOURCE_TEXT_ATTR*  pstaTextAttr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ulCharOffset`  
 in Die Position des Anfangs des Text Bereichs.  
  
 `cChars`  
 in Die Anzahl der Zeichen im Bereich.  
  
 `pstaTextAttr`  
 in Die Quell Text Attribute für den Textbereich.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Es ist ein Fehler, `SetTextAttributes` für einen Textbereich aufzurufen, bevor dieser Text dem Dokument hinzugefügt wird. Wenden Sie die Methoden `AddDBCSText`, `AddUnicodeText` oder `AddDeferredText` an, um dem Dokument Text hinzuzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugdocumenthelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)    
 [Idebugdocumenthelper:: addunicodetext](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)    
 [Idebugdocumenthelper:: adddbcstext](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [Idebugdocumenthelper:: adddeferredtext](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)