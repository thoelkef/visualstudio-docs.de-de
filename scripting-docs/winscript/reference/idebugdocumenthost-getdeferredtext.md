---
title: IDebugDocumentHost::GetDeferredText | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ace3bdbfef143a3307d81455788a1e81788cb50b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Gibt einen Bereich von Zeichen, die hinzugefügt wurden die `IDebugDocumentHelper::AddDeferredText` das Originaldokument Host-Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 [in] Host definiert Cookie, das die Startposition des Texts darstellt.  
  
 `pcharText`  
 [in, out] Text-Zeichenpuffer. Diese Methode gibt keinen Zeichen zurück, wenn dieser Parameter ist `NULL`.  
  
 `pstaTextAttr`  
 [in, out] Ein Attribut Zeichenpuffer. Diese Methode gibt keinen Attribute zurück, wenn dieser Parameter ist `NULL`.  
  
 `pcNumChars`  
 [in, out] Gibt die tatsächliche Anzahl von zurückgegebenen Zeichen/Attribute an. Dieser Parameter muss vor dem Aufrufen dieser Methode auf NULL festgelegt werden.  
  
 `cMaxChars`  
 [in] Die maximale Anzahl der zurückzugebenden Zeichen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Die Methode ist nicht implementiert.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gelegten `E_NOTIMPL`, wenn der Host nicht aufruft `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
>  Diese Methode gibt den Text aus dem Originaldokument zurück. Der Host ist nicht nachverfolgen Bearbeitungen oder andere Änderungen an das Dokument von.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHost-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)