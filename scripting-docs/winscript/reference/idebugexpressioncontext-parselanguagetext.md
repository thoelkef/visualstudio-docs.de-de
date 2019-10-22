---
title: Idebugexpressioncontext::P arselanguagetext | Microsoft-Dokumentation
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
ms.openlocfilehash: 0493adde76e029088b637be3c6aaf02c55caaace
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573156"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Erstellt einen debugausdruck für den angegebenen Text.  
  
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
 in Stellt den Text des Ausdrucks oder der Anweisung (en) bereit.  
  
 `nRadix`  
 [in] Zu verwendende Basis.  
  
 `pstrDelimiter`  
 in Das Trennzeichen für das Ende des Skript Blocks. Wenn `pstrCode` aus einem Stream von Text analysiert wird, verwendet der Host normalerweise ein Trennzeichen, z. b. zwei einfache Anführungszeichen (' '), um das Ende des Skript Blocks zu erkennen. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass der Skript-Engine in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) die Skript-Engine diese Informationen verwendet, hängt von der Skript-Engine ab. Legen Sie diesen Parameter auf `NULL` fest, wenn der Host kein Trennzeichen verwendet hat, um das Ende des Skript Blocks zu markieren.  
  
 `dwFlags`  
 in Kombination der folgenden Debug-textflags:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Gibt an, dass der Text ein Ausdruck ist und keine Anweisung. Dieses Flag kann sich darauf auswirken, wie der Text von einigen Sprachen analysiert wird.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Wenn ein Rückgabewert verfügbar ist, wird er vom Aufrufer verwendet.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Lassen Sie keine Nebeneffekte zu. Wenn dieses Flag festgelegt ist, sollte die Auswertung des Ausdrucks keinen Laufzeitzustand ändern.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Lässt während der Auswertung des Texts Breakpoints zu. Wenn dieses Flag nicht festgelegt ist, werden während der Auswertung des Texts Breakpoints ignoriert.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Ermöglicht Fehlerberichte während der Auswertung des Texts. Wenn dieses Flag nicht festgelegt ist, werden während der Auswertung keine Fehler an den Host gemeldet.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Gibt an, dass der Ausdruck zu einem Code Kontext ausgewertet werden soll, anstatt den Ausdruck selbst zu ausführen.|  
  
 `ppe`  
 vorgenommen Gibt den debugausdruck für den angegebenen Text zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erstellt einen debugausdruck für den angegebenen Text.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionContext-Schnittstelle](../../winscript/reference/idebugexpressioncontext-interface.md)