---
title: 'Idebugdocumumthost:: getdeferredtext | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 273b4eb52b7263d34c347dff3a00479945b809df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569423"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Gibt einen Bereich von Zeichen zurück, die mit der `IDebugDocumentHelper::AddDeferredText`-Methode im ursprünglichen Host Dokument hinzugefügt wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwTextStartCookie`  
 in Host definiertes Cookie, das die Anfangsposition des Texts darstellt.  
  
 `pcharText`  
 [in, out] Ein Zeichen Text Puffer. Diese Methode gibt keine Zeichen zurück, wenn dieser Parameter `NULL` ist.  
  
 `pstaTextAttr`  
 [in, out] Ein Zeichen Attribut Puffer. Diese Methode gibt keine Attribute zurück, wenn dieser Parameter `NULL` ist.  
  
 `pcNumChars`  
 [in, out] Gibt die tatsächliche Anzahl der zurückgegebenen Zeichen/Attribute an. Dieser Parameter muss auf 0 (null) festgelegt werden, bevor diese Methode aufgerufen wird.  
  
 `cMaxChars`  
 in Die maximale Anzahl von Zeichen, die zurückgegeben werden sollen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Die Methode ist nicht implementiert.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt möglicherweise `E_NOTIMPL` zurück, wenn der Host `IDebugDocumentHelper::AddDeferredText` nicht aufruft.  
  
> [!NOTE]
> Diese Methode gibt den Text aus dem ursprünglichen Dokument zurück. Der Host verfolgt keine Bearbeitungen oder andere Änderungen am Dokument.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugdocumeinthost-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)    
 [Idebugdocumenthelper:: adddeferredtext](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)