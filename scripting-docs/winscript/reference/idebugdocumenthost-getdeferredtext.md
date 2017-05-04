---
title: "IDebugDocumentHost::GetDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetDeferredText"
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetDeferredText
Gibt einen Bereich von Zeichen, die hinzugefügt wurden, indem die `IDebugDocumentHelper::AddDeferredText`\-Methode bei, im ursprünglichen Hostdokument zurück.  
  
## Syntax  
  
```  
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### Parameter  
 `dwTextStartCookie`  
 \[in\] Host\-definiertes Cookie, das die Anfangsposition des Texts darstellt.  
  
 `pcharText`  
 \[in, out\] a\-Zeichentextpuffer.  Diese Methode gibt keine Zeichen zurück, wenn dieser Parameter `NULL` ist.  
  
 `pstaTextAttr`  
 \[in, out\] a\-Zeichenattributpuffer.  Diese Methode gibt nicht Attribute zurück, wenn dieser Parameter `NULL` ist.  
  
 `pcNumChars`  
 \[in, out\] gibt die tatsächliche Anzahl der zurückgegebenen Zeichen\/Attributen an.  Dieser Parameter muss auf\) festgelegt werden, bevor diese Methode aufruft.  
  
 `cMaxChars`  
 \[in\] Die maximale Anzahl von Zeichen zurückgegeben.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Die Methode ist nicht implementiert.|  
  
## Hinweise  
 Diese Methode gibt möglicherweise `E_NOTIMPL` zurück, wenn der Host nicht `IDebugDocumentHelper::AddDeferredText` aufruft.  
  
> [!NOTE]
>  Diese Methode gibt den Text vom Originaldokument zurück.  Der Host behält nicht Bearbeitungen oder andere Änderungen am Dokument verfolgt.  
  
## Siehe auch  
 [IDebugDocumentHost\-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE\_TEXT\_ATTR\-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)