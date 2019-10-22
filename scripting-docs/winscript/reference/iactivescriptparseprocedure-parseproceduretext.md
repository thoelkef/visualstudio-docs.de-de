---
title: Iactivescriptparameterprocedure::P arabproceduretext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedure_ParseProcedureText
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53ed29c3e283af0f923590851cf9bf0655f7ac08
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561534"
---
# <a name="iactivescriptparseprocedureparseproceduretext"></a>IActiveScriptParseProcedure::ParseProcedureText
Analysiert die angegebene Code Prozedur und fügt die Prozedur zum Namespace hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrCode`  
 in Adresse des auszuwertenden Prozedur Texts. Die Darstellung dieser Zeichenfolge hängt von der Skriptsprache ab.  
  
 `pstrFormalParams`  
 in Adresse der formalen Parameternamen für die Prozedur. Die Parameternamen müssen mit den entsprechenden Trennzeichen für die Skript-Engine getrennt werden. Die Namen dürfen nicht in Klammern eingeschlossen werden.  
  
 `pstrProcedureName`  
 in Die Adresse des auszuteilenden Prozedur namens.  
  
 `pstrItemName`  
 in Adresse des Element namens, der den Kontext liefert, in dem die Prozedur ausgewertet werden soll. Wenn dieser Parameter `NULL` ist, wird der Code im globalen Kontext der Skript-Engine ausgewertet.  
  
 `punkContext`  
 [in] Adresse des Kontextobjekts. Dieses Objekt ist für die Verwendung in einer Debugumgebung reserviert, in der ein solcher Kontext möglicherweise vom Debugger bereitgestellt wird, um einen aktiven Laufzeitkontext darzustellen. Wenn dieser Parameter `NULL` ist, verwendet die Engine `pstrItemName`, um den Kontext zu identifizieren.  
  
 `pstrDelimiter`  
 in Adresse des Trenn Zeichens für das Ende der Prozedur. Wenn `pstrCode` aus einem Stream von Text analysiert wird, verwendet der Host normalerweise ein Trennzeichen, z. b. zwei einfache Anführungszeichen (' '), um das Ende der Prozedur zu erkennen. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass der Skript-Engine in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) die Skript-Engine diese Informationen verwendet, hängt von der Skript-Engine ab. Legen Sie diesen Parameter auf `NULL` fest, wenn der Host kein Trennzeichen verwendet hat, um das Ende der Prozedur zu markieren.  
  
 `dwSourceContextCookie`  
 in Der von der Anwendung definierte Wert, der zum Debuggen verwendet wird.  
  
 `ulStartingLineNumber`  
 [in] Nullbasierter Wert, der angibt, auf welcher Zeile die Analyse beginnt.  
  
 `dwFlags`  
 in Flags, die der Prozedur zugeordnet sind. Es kann eine Kombination dieser Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Gibt an, dass der Code in `pstrCode` ein Ausdruck ist, der den Rückgabewert der Prozedur darstellt. Standardmäßig kann der Code einen Ausdruck, eine Liste von Anweisungen oder alle anderen Elemente enthalten, die in einer Prozedur von der Skriptsprache zulässig sind.|  
|SCRIPTPROC_IMPLICIT_THIS|Gibt an, dass der `this` Zeiger im Bereich der Prozedur enthalten ist.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Gibt an, dass die übergeordneten Elemente des `this` Zeigers in den Gültigkeitsbereich der Prozedur eingeschlossen werden.|  
  
 `ppdisp`  
 vorgenommen Adresse des Zeigers für das Objekt, das die globalen Methoden und Eigenschaften des Skripts enthält. Wenn ein solches Objekt von der Skript-Engine nicht unterstützt wird, wird `NULL` zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt. Die Skript-Engine unterstützt keine Lauf Zeit Hinzufügung von Prozeduren zum Namespace.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. befindet sich die Skript-Engine im nicht initialisierten oder geschlossenen Zustand).|  
|`OLESCRIPT_E_SYNTAX`|In der Prozedur ist ein nicht spezifizierter Syntax Fehler aufgetreten.|  
|`S_FALSE`|Die Skript-Engine unterstützt kein dispatchobjekt. der `ppdisp`-Parameter ist auf `NULL` festgelegt.|  
  
## <a name="remarks"></a>Hinweise  
 Während dieses Aufrufes wird kein Skriptcode ausgewertet; Stattdessen wird die Prozedur in den Skript Status kompiliert, in dem Sie später von dem Skript aufgerufen werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)