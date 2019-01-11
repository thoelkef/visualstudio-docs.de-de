---
title: IActiveScriptParseProcedure32::ParseProcedureText | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e772d8276de5528f0aed25278a03725d09edb180
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090908"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
Die Prozedur angegebenen Code analysiert und fügt die Prozedur auf den Namespace.  
  
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
 [in] Adresse der Text der Prozedur zum Auswerten. Die Darstellung dieser Zeichenfolge hängt von der Skriptsprache ab.  
  
 `pstrFormalParams`  
 [in] Adresse der formale Parameternamen für die Prozedur. Die Parameternamen müssen mit den entsprechenden Trennzeichen für die Skript-Engine getrennt werden. Die Namen sollten nicht in Klammern eingeschlossen werden.  
  
 `pstrProcedureName`  
 [in] Adresse der Name der Prozedur, die analysiert werden.  
  
 `pstrItemName`  
 [in] Adresse des Elementnamens, der den Kontext angibt, in dem die Prozedur ist, ausgewertet werden soll. Wenn dieser Parameter ist `NULL`, der Code im globalen Kontext des Skriptmoduls ausgewertet wird.  
  
 `punkContext`  
 [in] Adresse des Kontextobjekts. Dieses Objekt ist für die Verwendung in einer Debugumgebung reserviert, in der ein solcher Kontext möglicherweise vom Debugger bereitgestellt wird, um einen aktiven Laufzeitkontext darzustellen. Wenn dieser Parameter ist `NULL`, verwendet die Engine `pstrItemName` auf den Kontext zu identifizieren.  
  
 `pstrDelimiter`  
 [in] Die Adresse des Trennzeichens Ende-des-Prozedur. Wenn `pstrCode` wird analysiert, die aus einem Stream von Text und einem Trennzeichen, der Host in der Regel verwendet, wie z. B. zwei Anführungszeichen ("), um das Ende der Prozedur erkennen einfache. Dieser Parameter gibt das vom Host verwendete Trennzeichen an, sodass der Skript-Engine in gewissem Umfang eine bedingte, primitive Vorverarbeitung ermöglicht wird (beispielsweise die Ersetzung eines einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) die Skript-Engine diese Informationen verwendet, hängt von der Skript-Engine ab. Legen Sie diesen Parameter `NULL` Wenn der Host ein einzeln verwendetes Trennzeichen nicht verwendet haben, um das Ende der Prozedur markieren.  
  
 `dwSourceContextCookie`  
 [in] Anwendung definierter Wert, der zum Debuggen verwendet wird.  
  
 `ulStartingLineNumber`  
 [in] Nullbasierter Wert, der angibt, auf welcher Zeile die Analyse beginnt.  
  
 `dwFlags`  
 [in] Flags, die mit der Prozedur. Es kann eine Kombination dieser Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Gibt an, dass der Code in `pstrCode` ist ein Ausdruck, der den Rückgabewert der Prozedur darstellt. Standardmäßig kann der Code ein Ausdruck, eine Liste mit Anweisungen oder alles andernfalls zulässig in einer Prozedur, durch die Skriptsprache enthalten.|  
|SCRIPTPROC_IMPLICIT_THIS|Gibt an, dass die `this` Zeiger in den Bereich der Prozedur enthalten ist.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Gibt an, die den übergeordneten Elementen von der `this` Zeiger in den Bereich der Prozedur enthalten sind.|  
  
 `ppdisp`  
 [out] Die Adresse des Zeigers für das Objekt, das globalen Methoden und Eigenschaften des Skripts enthalten. Wenn ein Objekt, von die Skript-Engine nicht unterstützt wird `NULL` zurückgegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt. Die Skript-Engine unterstützt keine Laufzeit-hinzufügen von Prozeduren auf den Namespace.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul im nicht initialisierten oder geschlossenen Zustand ist).|  
|`OLESCRIPT_E_SYNTAX`|Ein nicht spezifizierter Syntaxfehler trat in der Prozedur.|  
|`S_FALSE`|Die Skript-Engine unterstützt nicht die Dispatch-Objekt. die `ppdisp` Parametersatz zu `NULL`.|  
  
## <a name="remarks"></a>Hinweise  
 Kein Skriptcode wird während dieses Aufrufs ausgewertet; Stattdessen wird das Verfahren in den skriptzustand kompiliert, in dem sie das Skript später aufgerufen werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)