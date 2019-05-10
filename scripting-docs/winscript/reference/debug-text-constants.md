---
title: DEBUG_TEXT-Konstanten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2342555c4ee92b403aa01cc0ca15bb805f2b002e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955249"
---
# <a name="debugtext-constants"></a>DEBUG_TEXT-Konstanten
Während der verwendete [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Konstanten  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Gibt an, dass der Text ein Ausdruck ist und keine Anweisung. Dieses Flag kann sich darauf auswirken, wie der Text von einigen Sprachen analysiert wird.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Wenn ein Rückgabewert verfügbar ist, wird er vom Aufrufer verwendet.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Lässt keine Nebeneffekte zu. Wenn dieses Flag festgelegt ist, sollte die Auswertung des Ausdrucks keinen Laufzeitzustand ändern.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Erlaubt Haltepunkte während der Auswertung des Texts. Wenn dieses Flag nicht festgelegt ist, werden Haltepunkte während der Auswertung des Texts ignoriert.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Erlaubt Fehlerberichte während der Auswertung des Texts. Wenn dieses Flag nicht festgelegt ist, werden Fehler nicht während der Auswertung an den Host gemeldet.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Gibt an, dass der Ausdruck in einen Codekontext ausgewertet werden soll statt den Ausdruck auszuführen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)