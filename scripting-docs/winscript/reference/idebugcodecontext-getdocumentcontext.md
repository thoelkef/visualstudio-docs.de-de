---
title: "IDebugCodeContext::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCodeContext.GetDocumentContext
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugCodeContext::GetDocumentContext"
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCodeContext::GetDocumentContext
Gibt den Dokumentenkontext zurück, der diesem Codekontext zugeordnet ist.  
  
## Syntax  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### Parameter  
 `ppsc`  
 \[out\] Der Dokumentenkontext dieser zugeordnete Codekontext.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Für Textdokumente sollte der Zeichenpositionsbereich den Text für die gesamte Anweisung enthalten.  Dies ermöglicht es dem Debugger IDE, um die Stromquelleanweisung hervorzuheben.  
  
## Siehe auch  
 [IDebugCodeContext\-Schnittstelle](../../winscript/reference/idebugcodecontext-interface.md)