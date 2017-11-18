---
title: IDebugExpressionContext::ParseLanguageText | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpressionContext.ParseLanguageText
apilocation: jscript.dll
helpviewer_keywords: IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e455768b7d38096c64ab61f2b36aeba871ddf0bc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Erstellt einen Debug-Ausdruck für den angegebenen Text.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrCode`  
 [in] Stellt den Text des Ausdrucks bzw. der Anweisung(en).  
  
 `nRadix`  
 [in] Zu verwendende Basis.  
  
 `pstrDelimiter`  
 [in] Das Ende der Skriptblock-Trennzeichen. Wenn `pstrCode` wird analysiert, die aus einem Stream des Texts, verwendet der Host in der Regel ein Trennzeichen, z. B. zwei Anführungszeichen ("), um das Ende des Skriptblocks erkennen einfache. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass dem Skriptmodul in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) das scripting Modul verwendet diese Informationen hängen von dem Skriptmodul. Legen Sie diesen Parameter zu `NULL` Wenn der Host ein Trennzeichen nicht verwendet haben, um das Ende des Skriptblocks markieren.  
  
 `dwFlags`  
 [in] Die Kombination aus den folgenden Text Debugflags:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Gibt an, dass der Text ein Ausdruck ist und keine Anweisung. Dieses Flag kann sich darauf auswirken, wie der Text von einigen Sprachen analysiert wird.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Wenn ein Rückgabewert verfügbar ist, wird er vom Aufrufer verwendet.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Nebeneffekte sind nicht zulässig. Wenn dieses Flag festgelegt ist, sollte die Auswertung des Ausdrucks keinen Laufzeitzustand ändern.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Können Haltepunkte während der Auswertung des Texts an. Wenn dieses Flag nicht festgelegt ist, werden Haltepunkte während der Auswertung des Texts ignoriert.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Können Fehlerberichte während der Auswertung des Texts an. Wenn dieses Flag nicht festgelegt ist werden dann Fehler nicht an den Host während der Auswertung gemeldet.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Gibt an, dass der Ausdruck in einen Codekontext ausgewertet werden, statt den Ausdruck auszuführen|  
  
 `ppe`  
 [out] Gibt den Ausdruck "Debug" nach dem angegebenen Text.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erstellt einen Debug-Ausdruck für den angegebenen Text.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionContext-Schnittstelle](../../winscript/reference/idebugexpressioncontext-interface.md)