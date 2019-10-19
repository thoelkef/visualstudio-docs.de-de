---
title: 'Idebugdocumenthelper:: adddeferredtext | Microsoft-Dokumentation'
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
ms.openlocfilehash: 1aae73e44059b1f07fa4cb54f40cdcd12e564a8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577044"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Benachrichtigt das Hilfsobjekt, dass der angegebene Text verfügbar ist, stellt jedoch nicht die Zeichen bereit.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cChars`  
 in Anzahl von (Unicode) Zeichen, die hinzugefügt werden sollen.  
  
 `dwTextStartCookie`  
 in Host definiertes Cookie, das die Anfangsposition des Texts darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die Methode ist fehlgeschlagen.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermöglicht es dem Host, die Bereitstellung der zu addier enden Zeichen zu verzögern, bis Sie benötigt werden, und ermöglicht gleichzeitig dem Hilfsprogramm das Generieren präziser Benachrichtigungen und Größen Informationen. Der `dwTextStartCookie`-Parameter ist ein vom Host definiertes Cookie, das die Anfangsposition des Texts darstellt. Bei nachfolgenden Aufrufen von `IDebugDocumentText::GetText` muss dieses Cookie bereitgestellt werden. Beispielsweise könnte das Cookie in einem Host, der Text in DBCS darstellt, ein Byte Offset sein.  
  
 Es wird davon ausgegangen, dass ein einzelner Aufruf von `IDebugDocumentText::GetText` Zeichen aus mehreren Aufrufen an `AddDeferredText` abrufen kann. Hilfsklassen können auch mehrmals den gleichen Bereich von verzögerten Zeichen anfordern.  
  
> [!NOTE]
> Aufrufe von `AddDeferredText` sollten nicht mit Aufrufen von `AddUnicodeText` oder `AddDBCSText` gemischt werden. Wenn dies auftritt, wird `E_FAIL` zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugdocumenthelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)    
 [Idebugdocumenthelper:: addunicodetext](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)    
 [Idebugdocumenthelper:: adddbcstext](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)