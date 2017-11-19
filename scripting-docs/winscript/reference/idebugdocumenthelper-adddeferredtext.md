---
title: IDebugDocumentHelper::AddDeferredText | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.AddDeferredText
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c92909874429075bebc6a1f0a252573d049584e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Benachrichtigt, dass der angegebene Text verfügbar ist, aber es keine Zeichen bietet dem Hilfsprogramm.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cChars`  
 [in] Die Anzahl von (Unicode-) Zeichen hinzufügen.  
  
 `dwTextStartCookie`  
 [in] Host definiert Cookie, das die Startposition des Texts darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Fehler bei der Methode.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode kann der Host zum Bereitstellen der Zeichen hinzufügen, bis sie benötigt werden, während gleichzeitig das Hilfsprogramm zum Generieren von genau Benachrichtigungen und Informationen zur Datenbankgröße zurückstellen. Die `dwTextStartCookie` Parameter ist ein Cookie, definiert durch den Host, der die Anfangsposition des Texts darstellt. Nachfolgende Aufrufe `IDebugDocumentText::GetText` müssen dieses Cookie angeben. Beispielsweise konnte in einem Host, der Text in DBCS darstellt, das Cookie ein Byteoffset sein.  
  
 Es wird angenommen, dass ein einzelner Aufruf `IDebugDocumentText::GetText` erhalten Zeichen aus mehreren Aufrufen an `AddDeferredText`. Hilfsklassen können auch mehr als einmal für den gleichen Bereich des verzögerten Zeichen bitten.  
  
> [!NOTE]
>  Aufrufe von `AddDeferredText` sollten nicht durch Aufrufe von kombiniert `AddUnicodeText` oder `AddDBCSText`. In diesem Fall `E_FAIL` zurückgegeben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)