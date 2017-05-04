---
title: "IActiveScriptParse::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_AddScriptlet"
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::AddScriptlet
Fügt ein Codeskriptlet dem Skript hinzu.  Diese Methode wird in der Umgebung, in der beibehaltene Zustand des Skripts mit dem Hostdokument verflochten wird und der Host zum Wiederherstellen des Skripts zuständig ist, und nicht über eine `IPersist*`\-Schnittstelle verwendet.  Die primären Beispiele sind HTML\-Skriptsprachen, die die Skriptlets des Codes eingebettet im ermöglichen zu den systeminternen Ereignissen \(beispielsweise, ONCLICK\= angefügt werden HTML\-Dokument, " button1.text\='Exit"\).  
  
## Syntax  
  
```  
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
  
#### Parameter  
 `pstrDefaultName`  
 \[in\] Adresse eines mit dem Skriptlet zuzuordnen, bei.  Wenn das Skriptlet nicht Benennungsinformationen \(wie im ONCLICK\-Beispiel oben\) enthält, wird dieser Name verwendet, um das Skriptlet zu identifizieren.  Wenn dieser Parameter `NULL` ist, stellt das Skriptmodul einen eindeutigen Namen, ggf. erstellt.  
  
 `pstrCode`  
 \[in\] Adresse des Skriptlettexts hinzuzufügen.  Die Interpretation dieser Zeichenfolge hängt von der Skriptsprache ab.  
  
 `pstrItemName`  
 \[in\] zugeordnete Adresse eines Puffers, der den Elementnamen enthält, mit diesem Skriptlet zu.  Dieser Parameter, zusätzlich zu `pstrSubItemName`, identifiziert das Objekt, für das das Skriptlet ein Ereignishandler ist.  
  
 `pstrSubItemName`  
 \[in\] Adresse eines Puffers, der den Namen des `subobject` des Elements enthält, mit dem dieses Skriptlet zugeordnet wird, Dieser Name muss in den benannten Typinformationen des Elements gefunden werden.  Dieser Parameter ist NULL, wenn das Skriptlet dem benannten Element anstelle `subitem` zugeordnet werden soll.  Dieser Parameter, zusätzlich zu `pstrItemName`, identifiziert das bestimmte Objekt, für das das Skriptlet ein Ereignishandler ist.  
  
 `pstrEventName`  
 \[in\] Adresse eines Puffers, der den Namen des Ereignisses enthält, für das das Skriptlet ein Ereignishandler ist.  
  
 `pstrDelimiter`  
 \[in\] Ende\-vonSkriptlet Adresse des Trennzeichens.  Wenn der `pstrCode`\-Parameter von einem Stück Text analysiert wird, verwendet der Host in der Regel ein Trennzeichen, wie zwei einfache Anführungszeichen \("\), um das Ende des Skriptlets zu erkennen.  Dieser Parameter gibt das Trennzeichen an, den der Host verwendet, das Skriptmodul zulassen, um eine bedingte Vorverarbeiten von Primitiva bereitzustellen, \(beispielsweise ein einfaches Anführungszeichen \['\] mit zwei einfachen Anführungszeichen zur Verwendung als Trennzeichen\) ersetzt wird.  Genauer gesagt, wie \(und ob\) das Skriptmodul ausnutzt, sind diese Informationen im Skriptmodul ab.  Legen Sie diesen Parameter auf fest, um auf NULL, wenn der Host kein Trennzeichen verwendet, um das Ende des Skriptlets zu markieren.  
  
 `dwSourceContextCookie`  
 \[in\] Anwendung festgelegten Wert, der zum Debuggen verwendet wird.  
  
 `ulStartingLineNumber`  
 \[in\] beginnt nullbasierter Wert, der angibt, die die Analyse zeichnen, an.  
  
 `dwFlags`  
 \[in\] Flags in Zusammenhang mit dem Skriptlet.  Kann eine Kombination der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|SCRIPTTEXT\_ISVISIBLE|Gibt an, dass der Skripttext sichtbar \(und daher aufrufbar nach Namen\) als globale Methode im Namespace des Skripts sein sollte.|  
|SCRIPTTEXT\_ISPERSISTENT|Gibt an, dass der Code, der während des Aufrufs hinzugefügt wird, gespeichert werden soll, wenn das Skriptmodul \(beispielsweise, durch einen Aufruf `IPersist*::Save`\) gespeichert wird oder wenn das Skriptmodul über einen Übergang zurück zum initialisierten Zustand zurückgesetzt wird.  Weitere Informationen zu diesen Zustand, finden Sie Skriptmodul\-Zustände.|  
  
 `pbstrName` ,  
 \[out\] tatsächlicher Name verwendet, um das Skriptlet zu identifizieren.  Dies ist, in der Reihenfolge der Einstellung sein: ein Name explizit angegeben Skriptlettext im, im Standardnamen angegeben in `pstrDefaultName` oder in einem eindeutigen Namen synthetisiert durch das Skriptmodul.  
  
 `pexcepinfo` ,  
 \[out\] Adresse einer Struktur, die Ausnahmeinformationen enthält.  Diese Struktur ausgefüllt werden soll, wenn DISP\_E\_EXCEPTION zurückgegeben wird.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`DISP_E_EXCEPTION`|Eine Ausnahme tritt in der Analyse des Skriptlets auf.  Der `pexcepinfo`\-Parameter enthält Informationen über die Ausnahme.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt, das Skriptmodul unterstützt nicht das Hinzufügen von Ereignis\-sinkenden Skriptlets.|  
|`E_POINTER`|Ein ungültiger Zeiger wurde angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, ist das Skriptmodul noch nicht geladen wurde oder initialisiert wurden\) und fehlgeschlagen ist daher.|  
|`OLESCRIPT_E_INVALIDNAME`|Der Standardname, der angegeben wird, ist in dieser Skriptsprache ungültig.|  
|`OLESCRIPT_E_SYNTAX`|Ein nicht spezifizierter Syntaxfehler beim im Skriptlet auf.|  
  
## Siehe auch  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)