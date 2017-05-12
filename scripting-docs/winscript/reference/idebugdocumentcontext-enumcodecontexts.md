---
title: "IDebugDocumentContext::EnumCodeContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentContext.EnumCodeContexts
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentContext::EnumCodeContexts"
ms.assetid: fb0aa64e-c458-4ef1-bcd8-5cebdc972549
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentContext::EnumCodeContexts
Listet die Codekontexte auf, die mit diesem Dokumentenkontext zugeordnet werden.  
  
## Syntax  
  
```  
HRESULT EnumCodeContexts(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### Parameter  
 `ppescc`  
 \[out\] Die Codekontexte dieser zugeordnete Dokumentenkontext.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Ein Dokument wird normalerweise mit nur einem Codekontext zugeordnet, es sei denn, das Dokument einer Includedatei oder eine Vorlage ist.  
  
## Siehe auch  
 [IDebugDocumentContext\-Schnittstelle](../../winscript/reference/idebugdocumentcontext-interface.md)