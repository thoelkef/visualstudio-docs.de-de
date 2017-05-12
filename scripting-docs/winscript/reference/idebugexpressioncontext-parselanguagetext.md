---
title: "IDebugExpressionContext::ParseLanguageText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext.ParseLanguageText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext::ParseLanguageText"
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext::ParseLanguageText
Erstellt eine Multithread\-DLL Ausdruck für den angegebenen Text.  
  
## Syntax  
  
```  
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### Parameter  
 `pstrCode`  
 \[in\] stellt den Text des Ausdrucks oder der Anweisungen bereit.  
  
 `nRadix`  
 \[in\] auf Basis verwenden.  
  
 `pstrDelimiter`  
 \[in\] Das Ende\-von\-SkriptBlock Trennzeichen.  Wenn `pstrCode` aus einem Stream des Texts analysiert wird, verwendet der Host in der Regel ein Trennzeichen, wie zwei einfache Anführungszeichen \("\), um das Ende des Skriptblocks zu erkennen.  Dieser Parameter gibt das Trennzeichen an, den der Host verwendet, das Skriptmodul zulassen, um eine bedingte Vorverarbeiten von Primitiva bereitzustellen, \(beispielsweise ein einfaches Anführungszeichen \['\] mit zwei einfachen Anführungszeichen zur Verwendung als Trennzeichen\) ersetzt wird.  Genauer gesagt, wie \(und ob\) das Skriptmodul verwendet, sind diese Informationen im Skriptmodul ab.  Legen Sie diesen Parameter auf `NULL` fest, wenn der Host kein Trennzeichen verwendet, um das Ende des Skriptblocks zu markieren.  
  
 `dwFlags`  
 \[in\] kennzeichnet Kombination des folgenden Debug\- Text:  
  
|Konstante|Wert|Description|  
|---------------|----------|-----------------|  
|DEBUG\_TEXT\_ISEXPRESSION|0x00000001|Gibt an, dass der Text ein Ausdruck im Gegensatz zu einer Anweisung ist.  Dieses Flag wirkt sich auf die Methode, in der der Text durch mehrere Sprachen analysiert wird.|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|Wenn ein Rückgabewert verfügbar ist, wird er vom Aufrufer verwendet.|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|Lassen Sie keine Nebeneffekte.  Wenn dieses Flag festgelegt ist, sollte die Auswertung des Ausdrucks keinen Laufzeitzustand ändern.|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|Ermöglicht Haltepunkte während der Auswertung des Texts.  Wenn dieses Flag nicht auf festgelegt ist, werden Haltepunkte während der Auswertung des Texts ignoriert.|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|Ermöglicht Fehlerberichte während der Auswertung des Texts.  Wenn dieses Flag nicht auf festgelegt ist, werden Fehler nicht an den Host während der Auswertung gemeldet.|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|Gibt den Ausdruck ist, einen Codekontext, anstatt den an Ausdruck selbst ausführen ausgewertet werden|  
  
 `ppe`  
 \[out\] Gibt den Debug\- Ausdruck für den angegebenen Text zurück.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode erstellt eine Multithread\-DLL Ausdruck für den angegebenen Text.  
  
## Siehe auch  
 [IDebugExpressionContext\-Schnittstelle](../../winscript/reference/idebugexpressioncontext-interface.md)