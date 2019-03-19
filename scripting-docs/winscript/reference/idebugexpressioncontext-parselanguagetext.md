---
title: IDebugExpressionContext::ParseLanguageText | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50f9f398b9193c776f8e2a823b78ce7b8da438b1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153473"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Erstellt einen Debug-Ausdruck für den angegebenen Text.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
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
 [in] Stellt den Text des Ausdrucks oder -Anweisungen.  
  
 `nRadix`  
 [in] Zu verwendende Basis.  
  
 `pstrDelimiter`  
 [in] Das Ende der Skriptblock-Trennzeichen. Wenn `pstrCode` wird analysiert, die aus einem Stream von Text und einem Trennzeichen, der Host in der Regel verwendet, wie z. B. zwei Anführungszeichen ("), um das Ende der Skriptblock erkennen einfache. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass der Skript-Engine in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) die Skript-Engine-verwendet diese Informationen hängen von der Skript-Engine. Legen Sie diesen Parameter `NULL` Wenn der Host ein einzeln verwendetes Trennzeichen nicht verwendet haben, um das Ende des Skriptblocks markieren.  
  
 `dwFlags`  
 [in] Die Kombination der folgenden Flags der Debug-Text:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Gibt an, dass der Text ein Ausdruck ist und keine Anweisung. Dieses Flag kann sich darauf auswirken, wie der Text von einigen Sprachen analysiert wird.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Wenn ein Rückgabewert verfügbar ist, wird er vom Aufrufer verwendet.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Lassen Sie keine Nebeneffekte zu. Wenn dieses Flag festgelegt ist, sollte die Auswertung des Ausdrucks keinen Laufzeitzustand ändern.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Können Haltepunkte während der Auswertung des Texts an. Wenn dieses Flag nicht festgelegt ist, werden Haltepunkte während der Auswertung des Texts ignoriert.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Können Fehlerberichte während der Auswertung des Texts an. Wenn dieses Flag nicht festgelegt ist werden dann Fehler nicht an den Host während der Auswertung gemeldet.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Gibt an, dass der Ausdruck in einen Codekontext ausgewertet werden soll, statt den Ausdruck auszuführen|  
  
 `ppe`  
 [out] Gibt zurück, den Debug-Ausdruck für den angegebenen Text.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erstellt einen Debug-Ausdruck für den angegebenen Text.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionContext-Schnittstelle](../../winscript/reference/idebugexpressioncontext-interface.md)