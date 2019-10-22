---
title: Iactivescriptparameterprocedureold::P arserproceduretext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 116cbc7fac0d53b55c9766945d56ecebd27b6785
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577446"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analysiert die angegebene Code Prozedur und fügt dem namens Bereich eine anonyme Prozedur hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrCode`  
 in Der auszuwertende Prozedur Text. Die Darstellung dieser Zeichenfolge hängt von der Skriptsprache ab.  
  
 `pstrFormalParams`  
 in Formale Parameternamen für die Prozedur. Die Parameternamen müssen mit den entsprechenden Trennzeichen für die Skript-Engine getrennt werden. Die Namen dürfen nicht in Klammern eingeschlossen werden.  
  
 `pstrItemName`  
 in Der Name des benannten Elements, das den Kontext enthält, in dem die Prozedur ausgewertet werden soll. Wenn dieser Parameter `NULL` ist, wird der Code im globalen Kontext der Skript-Engine ausgewertet.  
  
 `punkContext`  
 in Das Kontext Objekt. Dieses Objekt ist für die Verwendung in einer Debugumgebung reserviert, in der ein solcher Kontext möglicherweise vom Debugger bereitgestellt wird, um einen aktiven Laufzeitkontext darzustellen. Wenn dieser Parameter `NULL` ist, verwendet die Engine `pstrItemName`, um den Kontext zu identifizieren.  
  
 `pstrDelimiter`  
 in Das Trennzeichen für das Ende der Prozedur. Wenn `pstrCode` aus einem Stream von Text analysiert wird, verwendet der Host normalerweise ein Trennzeichen, z. b. zwei einfache Anführungszeichen (' '), um das Ende der Prozedur zu erkennen. Dieser Parameter gibt das Trennzeichen an, das der Host verwendet hat, sodass die Skript-Engine einige bedingte, primitive Vorverarbeitung bereitstellen kann (z. b. das Ersetzen eines einfachen Anführungs Zeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) die Skript-Engine diese Informationen verwendet, hängt von der Skript-Engine ab. Legen Sie diesen Parameter auf `NULL` fest, wenn der Host kein Trennzeichen verwendet hat, um das Ende der Prozedur zu markieren.  
  
 `dwSourceContextCookie`  
 in Der von der Anwendung definierte Wert, der zum Debuggen verwendet wird.  
  
 `ulStartingLineNumber`  
 in NULL basierter Wert, der angibt, in welcher Zeile die Verarbeitung beginnt.  
  
 `dwFlags`  
 in Flags, die der Prozedur zugeordnet sind. Kann eine Kombination dieser Werte sein.  
  
|Konstante|Wert|Bedeutung|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Gibt an, dass der Code in `pstrCode` ein Ausdruck ist, der den Rückgabewert der Prozedur darstellt.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Gibt an, dass der `this` Zeiger im Bereich der Prozedur enthalten ist.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Gibt an, dass die übergeordneten Elemente des `this` Zeigers in den Gültigkeitsbereich der Prozedur eingeschlossen werden.|  
  
 `ppdisp`  
 vorgenommen Gibt einen DispatchWrapper zurück, bei dem die Standardmethode die Prozedur ist, die von dieser Methode analysiert wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt. Die Skript-Engine unterstützt keine Lauf Zeit Hinzufügung von Prozeduren zum Namespace.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. befindet sich die Skript-Engine im nicht initialisierten oder geschlossenen Zustand).|  
|`OLESCRIPT_E_SYNTAX`|In der Prozedur ist ein nicht spezifizierter Syntax Fehler aufgetreten.|  
|`S_FALSE`|Die Skript-Engine unterstützt kein dispatchobjekt. der `ppdisp`parameter ist auf `NULL` festgelegt.|  
  
## <a name="remarks"></a>Hinweise  
 Während dieses Aufrufes wird kein Skriptcode ausgewertet; Stattdessen wird die Prozedur in eine Methode auf `ppdisp` kompiliert, wo Sie später von dem Skript aufgerufen werden kann.  
  
 Diese Schnittstelle ist zugunsten der `IActiveScriptParseProcedure`-Schnittstelle veraltet. Die `IActiveScriptParseProcedure::ParseProcedureText`-Methode ähnelt dieser Methode, kann jedoch den Namen der Prozedur angeben. In allen Fällen sollten `IActiveScriptParseProcedure::ParseProcedureText` verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Iactivescriptparameanprocedureold-Schnittstelle](../../winscript/reference/iactivescriptparseprocedureold-interface.md)    
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)