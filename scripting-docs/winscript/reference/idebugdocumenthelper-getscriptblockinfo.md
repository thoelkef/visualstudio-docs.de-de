---
title: "IDebugDocumentHelper::GetScriptBlockInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.GetScriptBlockInfo
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::GetScriptBlockInfo"
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::GetScriptBlockInfo
Ruft den Bereich von Zeichen und von Skriptmodul entsprechend einem Skriptblock ab.  
  
## Syntax  
  
```  
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### Parameter  
 `dwSourceContext`  
 \[in\] Der Quellkontext für den Skriptblock.  
  
 `ppasd`  
 \[out\] Das Skriptmodul für diesen Skriptblock.  
  
 `piCharPos`  
 \[out\] Speicherort Start des Skriptblocks.  
  
 `cChars`  
 \[out\] Anzahl von Zeichen im Skriptblock.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode ruft den Zeichenbereich und von Skriptmodul entsprechend einem Skriptblock ab.  
  
## Siehe auch  
 [IDebugDocumentHelper\-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)