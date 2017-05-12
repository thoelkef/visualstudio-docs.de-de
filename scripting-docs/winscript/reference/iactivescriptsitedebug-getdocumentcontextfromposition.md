---
title: "IActiveScriptSiteDebug::GetDocumentContextFromPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetDocumentContextFromPosition"
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetDocumentContextFromPosition
Wird vom Sprachmodul, um `IDebugCodeContext::GetSourceContext` zu delegieren.  
  
## Syntax  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### Parameter  
 `dwSourceContext`  
 \[in\] Der Inhalt der Quelldatei wie geplant zu `ParseScriptText` oder zu `AddScriptlet`.  
  
 `uCharacterOffset`  
 \[in\] Zeichenoffset relativ zum Anfang des Skriptblocks oder des Skriptlets.  
  
 `uNumChars`  
 \[in\] Anzahl von Zeichen in diesem Kontext.  
  
 `ppsc`  
 \[out\] Der Dokumentenkontext entsprechend diesem Zeichenpositionsbereich.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Sprachmodule verwenden diese Methode, um `IDebugCodeContext::GetSourceContext` zu delegieren.  
  
## Siehe auch  
 [IActiveScriptSiteDebug\-Schnittstelle](../../winscript/reference/iactivescriptsitedebug-interface.md)