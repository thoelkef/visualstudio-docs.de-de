---
title: IActiveScriptParse::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_AddScriptlet
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e854ac71dc36263d805160f9336e049856076ce5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724650"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
Das Skript wird ein Code-Scriptlet hinzugefügt. Diese Methode wird verwendet, in Umgebungen, in dem die persistente Status des Skripts wird mit dem Hostdokument ineinander greifen und der Host ist verantwortlich für das Skript wiederherstellen, Umweg über ein `IPersist*` Schnittstelle. Die primäre Beispiele sind HTML-Skriptsprachen, mit denen Skriptlets Code eingebettet im HTML-Dokument an systeminterne Ereignisse angefügt werden können (z. B. ONCLICK="button1.text='Exit" ").  
  
## <a name="syntax"></a>Syntax  
  
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
  
#### <a name="parameters"></a>Parameter  
 `pstrDefaultName`  
 [in] Adresse des einen Standardnamen, dem Scriptlet zugeordnet werden soll. Wenn das Scriptlet keine Namensinformationen (wie im obigen ONCLICK-Beispiel) enthält, wird dieser Name zum Identifizieren des Scriptlets. Wenn dieser Parameter ist `NULL`, das Skriptmodul stellt einen eindeutigen Namen an, bei Bedarf.  
  
 `pstrCode`  
 [in] Die Adresse des Scriptlet-Texts hinzufügen. Die Darstellung dieser Zeichenfolge hängt von der Skriptsprache ab.  
  
 `pstrItemName`  
 [in] Die Adresse eines Puffers, der der Elementname diese Scriptlet zugeordnet enthält. Dieser Parameter, zusätzlich zu den `pstrSubItemName`, identifiziert das Objekt, das für die dem Scriptlet ein Ereignishandler ist.  
  
 `pstrSubItemName`  
 [in] Adresse eines Puffers, der den Namen der enthält einem `subobject` der den Namen des Elements mit dem dieser Scriptlet zugeordnet ist; dieser Name muss in der Typinformationen für das benannte Element gefunden werden. Dieser Parameter ist NULL, wenn das Scriptlet den Namen des Elements statt zugeordnet werden eine `subitem`. Dieser Parameter, zusätzlich zu den `pstrItemName`, identifiziert das Objekt für die dem Scriptlet ein Ereignishandler ist.  
  
 `pstrEventName`  
 [in] Die Adresse eines Puffers, der den Namen des Ereignisses enthält, für die dem Scriptlet ein Ereignishandler ist.  
  
 `pstrDelimiter`  
 [in] Adresse des end-of-scriptlet-Trennzeichens. Wenn die `pstrCode` Parameter aus einem Stream des Texts analysiert wird, verwendet der Host in der Regel ein Trennzeichen, z. B. zwei einfache von Anführungszeichen ("), um das Ende des Scriptlets zu erkennen. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass dem Skriptmodul in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) das Skriptmodul diese Informationen verwendet, hängt vom Skriptmodul ab. Legen Sie diesen Parameter auf NULL, wenn der Host ein Trennzeichen nicht verwendet haben, um das Ende des Scriptlets zu markieren.  
  
 `dwSourceContextCookie`  
 [in] Anwendungsdefinierten Wert, der für Debugzwecke verwendet wird.  
  
 `ulStartingLineNumber`  
 [in] Nullbasierter Wert, der angibt, auf welcher Zeile die Analyse beginnt.  
  
 `dwFlags`  
 [in] Flags, die dem Scriptlet zugeordnet sind. Eine Kombination der folgenden Werte ist möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Gibt an, dass der Skripttext sichtbar (und daher durch Namen aufgerufen werden kann) als globale Methode im Namespace des Skripts sein soll.|  
|SCRIPTTEXT_ISPERSISTENT|Gibt an, dass der Code, der während dieses Aufrufs hinzugefügt wird, gespeichert werden soll, wenn das Skriptmodul (beispielsweise durch einen Aufruf von `IPersist*::Save`) gespeichert wird oder wenn das Skriptmodul durch einen Übergang zurück zum initialisierten Zustand zurückgesetzt wird. Weitere Informationen zu diesem Zustand finden Sie in der Zustände der Skript-Modul.|  
  
 `pbstrName` ,  
 [out] Tatsächliche Name zum Identifizieren des Scriptlets verwendet. Wird verwendet, um in Prioritätsreihenfolge sein: ein Name explizit angegeben im Scriptlet-Texts, der Standardnamen in bereitgestellten `pstrDefaultName`, oder einen eindeutigen Namen, die vom Skriptmodul synthetisiert.  
  
 `pexcepinfo` ,  
 [out] Die Adresse einer Struktur mit Ausnahmeinformationen. Diese Struktur sollte gefüllt werden, wenn DISP_E_EXCEPTION zurückgegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`DISP_E_EXCEPTION`|Der Analyse des Scriptlets ist eine Ausnahme aufgetreten. Der `pexcepinfo`-Parameter enthält Informationen zur Ausnahme.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt. das Skriptmodul unterstützt keine Skriptlets Auffangen von Ereignissen hinzufügen.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul wurde noch kein geladen oder initialisiert) und konnte daher nicht.|  
|`OLESCRIPT_E_INVALIDNAME`|Der Standardname angegeben ist in dieser Skriptsprache ungültig.|  
|`OLESCRIPT_E_SYNTAX`|Ein nicht spezifizierter Syntaxfehler trat im Scriptlet auf.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)