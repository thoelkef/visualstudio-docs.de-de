---
title: 'IActiveScriptParse:: Addscriptlet | Microsoft-Dokumentation'
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
ms.openlocfilehash: 3b928efe2e8ac7bc0fbdb7c2ae9978a4418cbee7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090960"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
Das Skript wird ein Code-Scriptlet hinzugefügt. Diese Methode wird verwendet, in Umgebungen, in dem die persistente Status jenes Skripts ist eng mit dem Hostdokument verknüpft, und der Host ist verantwortlich für das Wiederherstellen von Skript, Umweg über ein `IPersist*` Schnittstelle. Die primäre Beispiele sind HTML-Skriptsprachen, mit denen Skriptlets eingebettet, die im HTML-Dokument an systeminterne Ereignisse angefügt werden können (z. B. ONCLICK="button1.text='Exit" ").  
  
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
 [in] Adresse des einen Standardnamen, dem Scriptlet zugeordnet werden soll. Enthält das Scriptlet keine Namensinformationen (wie im obigen ONCLICK-Beispiel), wird dieser Name zum Identifizieren des Scriptlets verwendet werden. Wenn dieser Parameter ist `NULL`, die Skript-Engine stellt einen eindeutigen Namen, falls erforderlich.  
  
 `pstrCode`  
 [in] Die Adresse des Scriptlet-Texts hinzufügen. Die Darstellung dieser Zeichenfolge hängt von der Skriptsprache ab.  
  
 `pstrItemName`  
 [in] Die Adresse eines Puffers, der den Namen des diesem Scriptlet zugeordnet enthält. Dieser Parameter enthält, zusätzlich zu den `pstrSubItemName`, identifiziert das Objekt, das für die das Scriptlet ein Ereignishandler ist.  
  
 `pstrSubItemName`  
 [in] Adresse eines Puffers, der den Namen des enthält eine `subobject` des benannten Elements mit dem diese Scriptlet zugeordnet ist; dieser Name muss in den Typinformationen für das benannte Element vorhanden sein. Dieser Parameter NULL ist, ist das Scriptlet, den Namen des Elements nicht zugeordnet werden soll eine `subitem`. Dieser Parameter enthält, zusätzlich zu den `pstrItemName`, identifiziert das bestimmte Objekt, das für die das Scriptlet ein Ereignishandler ist.  
  
 `pstrEventName`  
 [in] Die Adresse eines Puffers, der den Namen des Ereignisses enthält, für die das Scriptlet ein Ereignishandler ist.  
  
 `pstrDelimiter`  
 [in] Adresse des end-of-scriptlet-Trennzeichens. Wenn die `pstrCode` Parameter aus einem Stream des Texts analysiert wird, verwendet der Host in der Regel einem Trennzeichen, wie z. B. zwei einfache von Anführungszeichen ("), um das Ende des Scriptlets zu erkennen. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass der Skript-Engine in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) die Skript-Engine diese Informationen verwendet, hängt von der Skript-Engine ab. Legen Sie diesen Parameter auf NULL, wenn der Host ein einzeln verwendetes Trennzeichen nicht verwendet haben, um das Ende des Scriptlets zu markieren.  
  
 `dwSourceContextCookie`  
 [in] Anwendung definierter Wert, der zum Debuggen verwendet wird.  
  
 `ulStartingLineNumber`  
 [in] Nullbasierter Wert, der angibt, auf welcher Zeile die Analyse beginnt.  
  
 `dwFlags`  
 [in] Flags, die dem Scriptlet zugeordnet sind. Eine Kombination der folgenden Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Gibt an, dass der Skripttext sichtbar (und daher durch Namen aufgerufen werden kann) als globale Methode im Namespace des Skripts sein soll.|  
|SCRIPTTEXT_ISPERSISTENT|Gibt an, dass der Code, der während dieses Aufrufs hinzugefügt wird, gespeichert werden soll, wenn die Skript-Engine (beispielsweise durch einen Aufruf von `IPersist*::Save`) gespeichert wird oder wenn die Skript-Engine durch einen Übergang zurück zum initialisierten Zustand zurückgesetzt wird. Weitere Informationen zu diesem Zustand finden Sie in der Skript-Engine-Zuständen.|  
  
 `pbstrName` ,  
 [out] Tatsächliche Name zum Identifizieren des Scriptlets verwendet. In der Reihenfolge ihrer Priorität werden: ein Name explizit angegeben im Scriptlet-Texts, der Standardnamen in bereitgestellten `pstrDefaultName`, oder einen eindeutigen Namen, die von der Skript-Engine synthetisiert.  
  
 `pexcepinfo` ,  
 [out] Die Adresse einer Struktur mit Ausnahmeinformationen. Diese Struktur muss ausgefüllt werden, wenn DISP_E_EXCEPTION zurückgegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`DISP_E_EXCEPTION`|Bei der Analyse des Scriptlets ist eine Ausnahme aufgetreten. Der `pexcepinfo`-Parameter enthält Informationen zur Ausnahme.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt. die Skript-Engine unterstützt nicht das Auffangen von Ereignissen Skriptlets hinzufügen.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. die Skript-Engine wurde noch nicht wurden geladen oder initialisiert) und aus diesem Grund fehlgeschlagen ist.|  
|`OLESCRIPT_E_INVALIDNAME`|Der Standardname angegeben ist ungültig in diese Skriptsprache.|  
|`OLESCRIPT_E_SYNTAX`|Ein nicht spezifizierter Syntaxfehler trat im Scriptlet auf.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)