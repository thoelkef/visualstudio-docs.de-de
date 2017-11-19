---
title: IActiveScriptParseProcedure32::ParseProcedureText | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2f36160ab9dca3ccc99aed1068b7e94fe1b7675d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
Analysiert die angegebene Prozedur aus, und fügt die Prozedur den Namespace hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 [in] Adresse der Text der Prozedur um auszuwerten. Die Darstellung dieser Zeichenfolge hängt von der Skriptsprache ab.  
  
 `pstrFormalParams`  
 [in] Adresse des formale Parameternamen für die Prozedur. Die Parameternamen müssen mit den entsprechenden Trennzeichen für das Skriptmodul getrennt werden. Die Namen sollten nicht in Klammern eingeschlossen werden.  
  
 `pstrProcedureName`  
 [in] Adresse der Name der Prozedur, die analysiert werden.  
  
 `pstrItemName`  
 [in] Adresse des Elementnamens, der den Kontext angibt, in dem die Prozedur ausgewertet werden. Wenn dieser Parameter ist `NULL`, der Code im globalen Kontext des Skriptmoduls ausgewertet wird.  
  
 `punkContext`  
 [in] Adresse des Kontextobjekts. Dieses Objekt ist für die Verwendung in einer Debugumgebung reserviert, in der ein solcher Kontext möglicherweise vom Debugger bereitgestellt wird, um einen aktiven Laufzeitkontext darzustellen. Wenn dieser Parameter ist `NULL`, verwendet das Modul `pstrItemName` an den Kontext zu identifizieren.  
  
 `pstrDelimiter`  
 [in] Die Adresse des Trennzeichens Ende der Prozedur. Wenn `pstrCode` analysiert aus einem Stream des Texts und ein Trennzeichen vom Host in der Regel verwendet, z. B. zwei einfache von Anführungszeichen ("), um das Ende der Prozedur zu erkennen. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass dem Skriptmodul in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) das Skriptmodul diese Informationen verwendet, hängt vom Skriptmodul ab. Legen Sie diesen Parameter zu `NULL` Wenn der Host ein Trennzeichen nicht verwendet haben, um das Ende der Prozedur zu kennzeichnen.  
  
 `dwSourceContextCookie`  
 [in] Anwendungsdefinierten Wert, der für Debugzwecke verwendet wird.  
  
 `ulStartingLineNumber`  
 [in] Nullbasierter Wert, der angibt, auf welcher Zeile die Analyse beginnt.  
  
 `dwFlags`  
 [in] Flags, die die Prozedur zugeordnet werden. Es kann eine Kombination dieser Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Gibt an, dass der Code in `pstrCode` ist ein Ausdruck, den Rückgabewert der Prozedur darstellt. Standardmäßig kann der Code einen Ausdruck, der eine Liste von Anweisungen oder nichts sonst in einer Prozedur Skriptsprache zulässig enthalten.|  
|SCRIPTPROC_IMPLICIT_THIS|Gibt an, dass die `this` Zeiger in den Bereich der Prozedur enthalten ist.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Gibt an, die den übergeordneten Elementen von der `this` Zeiger in den Bereich der Prozedur enthalten sind.|  
  
 `ppdisp`  
 [out] Die Adresse des Zeigers für das Objekt, des Skripts globale Methoden und Eigenschaften enthält. Wenn das Skriptmodul solches Objekt nicht unterstützt `NULL` zurückgegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt. Das Skriptmodul wird zur Laufzeit-hinzufügen von Prozeduren, damit der Namespace nicht unterstützt.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul im nicht initialisierten oder geschlossenen Zustand ist).|  
|`OLESCRIPT_E_SYNTAX`|Ein nicht spezifizierter Syntaxfehler trat in der Prozedur.|  
|`S_FALSE`|Das Skriptmodul unterstützt keine Dispatch-Objekt; die `ppdisp` Parametersatz auf `NULL`.|  
  
## <a name="remarks"></a>Hinweise  
 Kein Skriptcode wird während dieses Aufrufs ausgewertet; Stattdessen wird die Prozedur in den skriptzustand kompiliert, in dem sie das Skript später aufgerufen werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)