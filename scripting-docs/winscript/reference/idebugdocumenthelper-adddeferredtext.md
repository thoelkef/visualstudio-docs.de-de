---
title: "IDebugDocumentHelper::AddDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddDeferredText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddDeferredText"
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddDeferredText
Benachrichtigt die Hilfe, dass der angegebene Text verfügbar ist, es bietet aber nicht die Zeichen.  
  
## Syntax  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### Parameter  
 `cChars`  
 \[in\] Zahl \(Unicode\) gelten andere Zeichen hinzuzufügen.  
  
 `dwTextStartCookie`  
 \[in\] Host\-definiertes Cookie, das die Anfangsposition des Texts darstellt.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die Methode verlassen.|  
  
## Hinweise  
 Diese Methode ermöglicht es dem Host, um die Zeichen zu verzögern, um hinzuzufügen, bis sie benötigt werden, beim Ermöglichen der Hilfe, um genaue Benachrichtigungen und Größe zu generieren.  Der `dwTextStartCookie`\-Parameter ist ein Cookie, definiert vom Host, der die Anfangsposition des Texts darstellt.  Nachfolgende Aufrufe von `IDebugDocumentText::GetText` müssen dieses Cookie bereitstellen.  Bei einem Host, der Text in DBCS darstellt, kann das Cookie ein Byte ausgeglichen sein.  
  
 Es wird davon ausgegangen, dass ein einzelner Aufruf `IDebugDocumentText::GetText` Zeichen von mehreren Aufrufen an `AddDeferredText` erhalten.  Hilfsklassen anfordern kann auch um denselben Bereich von verzögerten Zeichen mehrmals.  
  
> [!NOTE]
>  Aufrufe `AddDeferredText` sollten nicht durch Aufrufe von `AddUnicodeText` oder zu `AddDBCSText` kombiniert werden.  Wenn dies auftritt, wird `E_FAIL` zurückgegeben.  
  
## Siehe auch  
 [IDebugDocumentHelper\-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)