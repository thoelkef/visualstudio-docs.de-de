---
title: 'IActiveScriptParse:: Parsescripttext | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_ParseScriptText
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d88258a1bd16dba1de8d6ffa282f0f8ba409e2d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088971"
---
# <a name="iactivescriptparseparsescripttext"></a>IActiveScriptParse::ParseScriptText
Analysiert das angegebene Code-Scriptlet, fügt Deklarationen im Namespace hinzu und wertet, wo angebracht, Code aus.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>Parameter  
  
|||  
|-|-|  
|`pstrCode`|[in] Adresse des auszuwertenden Scriptlet-Texts. Die Darstellung dieser Zeichenfolge hängt von der Skriptsprache ab.|  
|`pstrItemName`|[in] Adresse des Elementnamens, der den Kontext angibt, in dem das Scriptlet ausgewertet werden soll. Wenn dieser Parameter NULL ist, wird der Code im globalen Kontext der Skript-Engine ausgewertet.|  
|`punkContext`|[in] Adresse des Kontextobjekts. Dieses Objekt ist für die Verwendung in einer Debugumgebung reserviert, in der ein solcher Kontext möglicherweise vom Debugger bereitgestellt wird, um einen aktiven Laufzeitkontext darzustellen. Wenn dieser Parameter NULL ist, verwendet die Engine `pstrItemName`, um den Kontext zu identifizieren.|  
|`pstrDelimiter`|[in] Adresse des end-of-scriptlet-Trennzeichens. Wenn `pstrCode` von einem Stream des Texts analysiert wird, verwendet der Host in der Regel ein Trennzeichen, wie beispielsweise zwei einfache Anführungszeichen ("), um das Ende des Scriptlets zu erkennen. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass der Skript-Engine in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) die Skript-Engine diese Informationen verwendet, hängt von der Skript-Engine ab. Legen Sie diesen Parameter auf `NULL` fest, wenn der Host kein Trennzeichen verwendete, um das Ende des Scriptlets zu markieren.|  
|`dwSourceContextCookie`|[in] Cookie, das zu Debugzwecken verwendet wird.|  
|`ulStartingLineNumber`|[in] Nullbasierter Wert, der angibt, auf welcher Zeile die Analyse beginnt.|  
|`dwFlags`|[in] Flags, die dem Scriptlet zugeordnet sind. Es kann eine Kombination dieser Werte sein:|  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Wenn der Unterschied zwischen einem rechnerischen Ausdruck und einer Anweisung wichtig, aber von der Syntax in der Skriptsprache her doppeldeutig ist, gibt dieses Flag an, dass das Scriptlet als ein Ausdruck zu interpretieren ist, statt einer Anweisung oder einer Liste von Anweisungen. Standardmäßig werden Anweisungen angenommen, es sei denn, dass die richtige Auswahl vom Syntax des Scriptlet-Texts her bestimmt werden kann.|  
|SCRIPTTEXT_ISPERSISTENT|Gibt an, dass der Code, der während dieses Aufrufs hinzugefügt wird, gespeichert werden soll, wenn die Skript-Engine (beispielsweise durch einen Aufruf von `IPersist*::Save`) gespeichert wird oder wenn die Skript-Engine durch einen Übergang zurück zum initialisierten Zustand zurückgesetzt wird.|  
|SCRIPTTEXT_ISVISIBLE|Gibt an, dass der Skripttext sichtbar (und daher durch Namen aufgerufen werden kann) als globale Methode im Namespace des Skripts sein soll.|  
  
|||  
|-|-|  
|`pvarResult`|[out] Adresse eines Puffers, der die Ergebnisse des Scriptlet-Verarbeitung empfängt oder `NULL`, wenn der Aufrufer kein Ergebnis erwartet (das heißt, dass der SCRIPTTEXT_ISEXPRESSIONS-Wert nicht festgelegt ist).|  
|`pexcepinfo`|[out] Adresse einer Struktur, die Ausnahmeinformationen erhält. Diese Struktur wird ausgefüllt, wenn `IActiveScriptParse::ParseScriptText` DISP_E_EXCEPTION zurückgibt.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`DISP_E_EXCEPTION`|Eine Ausnahme tritt bei der Verarbeitung des Scriptlets auf. Der `pexcepinfo`-Parameter enthält Informationen zur Ausnahme.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt. Die Skript-Engine unterstützt keine Laufzeitauswertung von Ausdrücken oder Anweisungen.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (beispielsweise, wenn die Skript-Engine im nicht initialisierten oder geschlossenen Zustand ist oder der SCRIPTTEXT_ISEXPRESSIONS-Flag festgelegt war und sich die Skript-Engine im initialisierten Zustand befindet).|  
|`OLESCRIPT_E_SYNTAX`|Ein nicht spezifizierter Syntaxfehler trat im Scriptlet auf.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Skript-Engine im initialisierten Zustand ist, wird kein Code tatsächlich während dieses Aufrufs ausgewertet; dieser Code wird vielmehr in die Warteschlange gestellt und ausgeführt, wenn die Skript-Engine in den gestarteten Zustand übergehen soll. Da die Ausführung im initialisierten Zustand nicht zulässig ist, ist es ein Fehler, diese Methode mit dem SCRIPTTEXT_ISEXPRESSIONS-Flag aufzurufen, wenn im initialisierten Zustand.  
  
 Das Scriptlet kann ein Ausdruck, eine Liste mit Anweisungen oder alles sein, das für die verwendete Skriptsprache zulässig ist. Diese Methode wird beispielsweise bei der Auswertung der HTML-Code verwendet \<Skript >-Tag, wodurch Anweisungen ausgeführt werden, weil die HTML-Seite erstellt wird, anstatt nur in den skriptzustand zu kompilieren,.  
  
 Der Code, der an diese Methode übergeben wird, muss ein gültiger, vollständiger Teil des Codes sein. Beispielsweise ist es in VBScript nicht zulässig, diese Methode einmal mit "Sub Function(x)" aufzurufen und dann ein zweites Mal mit `End Sub`. Der Parser darf nicht auf den zweiten Aufruf warten, um die Unterroutine abzuschließen. Er muss stattdessen einen Analysefehler generieren, da eine Unterroutinendeklaration gestartet, aber nicht abgeschlossen wurde.  
  
 Weitere Informationen über skriptzustände finden Sie im Abschnitt "Skriptmodulzustände" der [Windows Script-Engines](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)