---
title: "IDebugDocumentHelper::AddDBCSText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddDBCSText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddDBCSText"
ms.assetid: 5e5011b2-bbb4-491b-9a11-eb2846be44aa
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddDBCSText
Fügt eine DBCS\-Zeichenfolge am Ende dieses Dokuments an.  
  
## Syntax  
  
```  
HRESULT AddDBCSText(  
   LPCSTR  pszText  
);  
```  
  
#### Parameter  
 `pszText`  
 \[in\] Zeiger auf eine auf NULL endende Zeichenfolge, die den Text enthält.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die Methode war nicht möglich, die Zeichen hinzuzufügen.|  
  
## Hinweise  
 Diese Methode generiert `IDebugDocumentTextEvents` Benachrichtigungen.  
  
> [!NOTE]
>  Wenn diese Methode aufgerufen wird, nachdem `IDebugDocumentHelper::AddDeferredText` aufgerufen wurde, wird `E_FAIL` zurückgegeben.  
  
## Siehe auch  
 [IDebugDocumentHelper\-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [IDebugDocumentTextEvents\-Schnittstelle](../../winscript/reference/idebugdocumenttextevents-interface.md)