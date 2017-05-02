---
title: "IProvideExpressionContexts::EnumExpressionContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProvideExpressionContexts.EnumExpressionContexts
apilocation: jscript.dll
helpviewer_keywords: 
  - "IProvideExpressionContexts::EnumExpressionContexts"
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProvideExpressionContexts::EnumExpressionContexts
Gibt einen Enumerator von den Ausdruckskontexten zurück, die von dieser Komponente bezeichnet werden.  
  
## Syntax  
  
```  
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### Parameter  
 `ppedec`  
 \[out\] Ein Enumerator von den Ausdruckskontexten wird von dieser Komponente.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Der Debug\- ProzessManager verwendet diese Methode, um alle globalen Ausdruckskontexte zu suchen, die mit einem angegebenen Thread zugeordnet werden.  
  
> [!NOTE]
>  Diese Methode wird aus dem Thread relevante bezeichnet.  Sie ist von der Implementierung, um des aktuellen Threads ermitteln und eines entsprechenden Enumerators zurückzugeben.  
  
## Siehe auch  
 [IProvideExpressionContexts\-Schnittstelle](../../winscript/reference/iprovideexpressioncontexts-interface.md)