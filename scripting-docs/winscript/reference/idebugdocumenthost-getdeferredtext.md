---
title: 'Idebugdocumenthost:: Getdeferredtext | Microsoft-Dokumentation'
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
ms.openlocfilehash: 3e5800a6de15d2d59208022fa44d3c2f4c931e14
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446568"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Gibt einen Bereich von Zeichen, die mithilfe von hinzugefügt wurden die `IDebugDocumentHelper::AddDeferredText` Methode im ursprünglichen Hostdokument.  
  
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
 [in] Host definierten Cookie, das die Anfangsposition des Texts darstellt.  
  
 `pcharText`  
 [in, out] Einen Zeichenpuffer Text. Diese Methode gibt nicht die Zeichen zurück, wenn dieser Parameter ist `NULL`.  
  
 `pstaTextAttr`  
 [in, out] Einen Zeichenpuffer-Attribut. Diese Methode gibt nicht die Attribute zurück, wenn dieser Parameter ist `NULL`.  
  
 `pcNumChars`  
 [in, out] Gibt an, die tatsächliche Anzahl der Zeichen/Attribute zurückgegeben. Dieser Parameter muss 0 (null) vor dem Aufrufen dieser Methode festgelegt werden.  
  
 `cMaxChars`  
 [in] Die maximale Anzahl der zurückzugebenden Zeichen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Die Methode ist nicht implementiert.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode zurückgeben kann `E_NOTIMPL`, wenn der Host nicht aufruft `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
> Diese Methode gibt den Text des ursprünglichen Dokuments zurück. Der Host ist nicht von verfolgt werden Änderungen oder andere Änderungen am Dokument.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHost-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)