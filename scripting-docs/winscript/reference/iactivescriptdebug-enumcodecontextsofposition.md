---
title: "IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::EnumCodeContextsOfPosition"
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::EnumCodeContextsOfPosition
Wird durch einen Smarthost, um die `IDebugDocumentContext::EnumCodeContexts`\-Methode zu delegieren.  
  
## Syntax  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### Parameter  
 `dwSourceContext`  
 \[in\] Der Quellkontext wie geplant zu `IActiveScriptParse::ParseScriptText` oder zu `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 \[in\] Zeichenoffset relativ zum Anfang des Skripttexts.  
  
 `uNumChars`  
 \[in\] Anzahl von Zeichen in diesem Kontext.  
  
 `ppescc`  
 \[out\] Ein Enumerator der Codekontexte im angegebenen Bereich.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Smarthosts verwenden diese Methode, um die `IDebugDocumentContext::EnumCodeContexts`\-Methode zu delegieren.  
  
## Siehe auch  
 [IActiveScriptDebug\-Schnittstelle](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)