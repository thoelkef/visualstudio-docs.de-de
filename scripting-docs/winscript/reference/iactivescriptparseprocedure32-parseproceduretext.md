---
title: IActiveScriptParseProcedure32::P AR. proceduretext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 52333d13731b5c31329ee812be403c09cf43d63b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835731"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
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
 in Adresse des Element namens, der den Kontext liefert, in dem die Prozedur ausgewertet werden soll. Wenn dieser Parameter ist `NULL` , wird der Code im globalen Kontext der Skript-Engine ausgewertet.  
  
 `punkContext`  
 [in] Adresse des Kontextobjekts. Dieses Objekt ist für die Verwendung in einer Debugumgebung reserviert, in der ein solcher Kontext möglicherweise vom Debugger bereitgestellt wird, um einen aktiven Laufzeitkontext darzustellen. Wenn dieser Parameter ist `NULL` , verwendet die Engine, `pstrItemName` um den Kontext zu identifizieren.  
  
 `pstrDelimiter`  
 in Adresse des Trenn Zeichens für das Ende der Prozedur. Wenn `pstrCode` aus einem Stream von Text analysiert wird, verwendet der Host normalerweise ein Trennzeichen, z. b. zwei einfache Anführungszeichen (' '), um das Ende der Prozedur zu erkennen. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass der Skript-Engine in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) die Skript-Engine diese Informationen verwendet, hängt von der Skript-Engine ab. Legen Sie diesen Parameter auf fest, `NULL` Wenn der Host kein Trennzeichen verwendet hat, um das Ende der Prozedur zu markieren.  
  
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
 vorgenommen Adresse des Zeigers für das Objekt, das die globalen Methoden und Eigenschaften des Skripts enthält. Wenn ein solches Objekt von der Skript-Engine nicht unterstützt wird, `NULL` wird zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolg.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt. Die Skript-Engine unterstützt keine Lauf Zeit Hinzufügung von Prozeduren zum Namespace.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. befindet sich die Skript-Engine im nicht initialisierten oder geschlossenen Zustand).|  
|`OLESCRIPT_E_SYNTAX`|In der Prozedur ist ein nicht spezifizierter Syntax Fehler aufgetreten.|  
|`S_FALSE`|Die Skript-Engine unterstützt kein dispatchobjekt. der- `ppdisp` Parameter ist auf festgelegt `NULL` .|  
  
## <a name="remarks"></a>Hinweise  
 Während dieses Aufrufes wird kein Skriptcode ausgewertet; Stattdessen wird die Prozedur in den Skript Status kompiliert, in dem Sie später von dem Skript aufgerufen werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)