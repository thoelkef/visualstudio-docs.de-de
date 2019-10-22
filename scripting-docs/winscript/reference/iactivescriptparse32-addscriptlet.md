---
title: 'IActiveScriptParse32:: addscriptlet | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fcf11eb2-8e71-4cca-afda-a91791c243ff
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b48d89ce2c49bd971fe298d2b4773aad8b65e8c3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561696"
---
# <a name="iactivescriptparse32addscriptlet"></a>IActiveScriptParse32:: addscriptlet
Fügt dem Skript ein Code-Scriptlet hinzu. Diese Methode wird in Umgebungen verwendet, in denen der persistente Zustand des Skripts mit dem Host Dokument verknüpft ist und der Host für die Wiederherstellung des Skripts zuständig ist, nicht über eine `IPersist*`-Schnittstelle. Die wichtigsten Beispiele sind HTML-Skriptsprachen, die es ermöglichen, dass Skripts, die im HTML-Dokument eingebettet sind, an systeminterne Ereignisse angefügt werden (z. Button1. OnClick = ". Text = ' Exit '").  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrDefaultName`  
 in Adresse eines Standard namens, der dem Scriptlet zugeordnet werden soll. Wenn das Scriptlet keine Benennungs Informationen enthält (wie im obigen OnClick-Beispiel), wird dieser Name zur Identifizierung des Scriptlets verwendet. Wenn dieser Parameter `NULL` ist, stellt die Skript-Engine ggf. einen eindeutigen Namen her.  
  
 `pstrCode`  
 in Adresse des hinzu zufügenden Scriptlet-Texts. Die Darstellung dieser Zeichenfolge hängt von der Skriptsprache ab.  
  
 `pstrItemName`  
 in Adresse eines Puffers, der den diesem Scriptlet zugeordneten Elementnamen enthält. Dieser Parameter identifiziert zusätzlich zu `pstrSubItemName` das Objekt, für das das Scriptlet ein Ereignishandler ist.  
  
 `pstrSubItemName`  
 in Adresse eines Puffers, der den Namen eines `subobject` des benannten Elements enthält, mit dem dieses Scriptlet verknüpft ist. Dieser Name muss in den Typinformationen des benannten Elements gefunden werden. Dieser Parameter ist NULL, wenn das Scriptlet dem benannten Element anstelle einer `subitem` zugeordnet werden soll. Dieser Parameter identifiziert zusätzlich zu `pstrItemName` das spezifische Objekt, für das das Scriptlet ein Ereignishandler ist.  
  
 `pstrEventName`  
 in Adresse eines Puffers, der den Namen des Ereignisses enthält, für das das Scriptlet ein Ereignishandler ist.  
  
 `pstrDelimiter`  
 [in] Adresse des end-of-scriptlet-Trennzeichens. Wenn der `pstrCode`-Parameter aus einem Stream von Text analysiert wird, verwendet der Host normalerweise ein Trennzeichen, z. b. zwei einfache Anführungszeichen (' '), um das Ende des Scriptlets zu erkennen. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass der Skript-Engine in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) die Skript-Engine diese Informationen verwendet, hängt von der Skript-Engine ab. Legen Sie diesen Parameter auf NULL fest, wenn der Host kein Trennzeichen verwendet hat, um das Ende des Scriptlets zu markieren.  
  
 `dwSourceContextCookie`  
 in Der von der Anwendung definierte Wert, der zum Debuggen verwendet wird.  
  
 `ulStartingLineNumber`  
 [in] Nullbasierter Wert, der angibt, auf welcher Zeile die Analyse beginnt.  
  
 `dwFlags`  
 [in] Flags, die dem Scriptlet zugeordnet sind. Kann eine Kombination der folgenden Werte sein:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Gibt an, dass der Skripttext sichtbar (und daher durch Namen aufgerufen werden kann) als globale Methode im Namespace des Skripts sein soll.|  
|SCRIPTTEXT_ISPERSISTENT|Gibt an, dass der Code, der während dieses Aufrufs hinzugefügt wird, gespeichert werden soll, wenn die Skript-Engine (beispielsweise durch einen Aufruf von `IPersist*::Save`) gespeichert wird oder wenn die Skript-Engine durch einen Übergang zurück zum initialisierten Zustand zurückgesetzt wird. Weitere Informationen zu diesem Status finden Sie unter Status der Skript-Engine.|  
  
 `pbstrName` ,  
 vorgenommen Tatsächlicher Name, der zum Identifizieren des Scriptlets verwendet wird. Dies ist die bevorzugte Reihenfolge: ein Name, der explizit im Scriptlet-Text angegeben ist, der in `pstrDefaultName` angegebene Standardname oder ein eindeutiger Name, der von der Skript-Engine synthetisiert wird.  
  
 `pexcepinfo` ,  
 vorgenommen Adresse einer Struktur, die Ausnahme Informationen enthält. Diese Struktur sollte ausgefüllt werden, wenn DISP_E_EXCEPTION zurückgegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`DISP_E_EXCEPTION`|Ausnahme bei der Verarbeitung des Scriptlet. Der `pexcepinfo`-Parameter enthält Informationen zur Ausnahme.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt. die Skript-Engine unterstützt nicht das Hinzufügen von Scriptlets, bei denen das Ereignis sinkt|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. wurde die Skript-Engine noch nicht geladen oder initialisiert) und ist daher fehlgeschlagen.|  
|`OLESCRIPT_E_INVALIDNAME`|Der angegebene Standardname ist in dieser Skriptsprache ungültig.|  
|`OLESCRIPT_E_SYNTAX`|Ein nicht spezifizierter Syntaxfehler trat im Scriptlet auf.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)