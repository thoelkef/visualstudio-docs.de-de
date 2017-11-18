---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptParseProcedureOld.ParseProcedureText
apilocation: jscript.dll
helpviewer_keywords: IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab546deb390535fa8ff71e116a0ad42d33cc104
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Die Prozedur angegebenen Code analysiert, und fügt eine anonyme Prozedur Namespace hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 [in] Der Text der Prozedur um auszuwerten. Die Darstellung dieser Zeichenfolge hängt von der Skriptsprache ab.  
  
 `pstrFormalParams`  
 [in] Formale Parameternamen für die Prozedur. Die Parameternamen müssen mit den entsprechenden Trennzeichen für das Skriptmodul getrennt werden. Die Namen sollten nicht in Klammern eingeschlossen werden.  
  
 `pstrItemName`  
 [in] Der Name des benannten Elements, das den Kontext angibt, in dem die Prozedur ausgewertet werden. Wenn dieser Parameter ist `NULL`, der Code im globalen Kontext des Skriptmoduls ausgewertet wird.  
  
 `punkContext`  
 [in] Das Context-Objekt. Dieses Objekt ist für die Verwendung in einer Debugumgebung reserviert, in der ein solcher Kontext möglicherweise vom Debugger bereitgestellt wird, um einen aktiven Laufzeitkontext darzustellen. Wenn dieser Parameter ist `NULL`, verwendet das Modul `pstrItemName` an den Kontext zu identifizieren.  
  
 `pstrDelimiter`  
 [in] Das Ende der Prozedur-Trennzeichen. Wenn `pstrCode` analysiert aus einem Stream des Texts und ein Trennzeichen vom Host in der Regel verwendet, z. B. zwei einfache von Anführungszeichen ("), um das Ende der Prozedur zu erkennen. Dieser Parameter gibt das Trennzeichen an, die vom Host verwendete, sodass dem Skriptmodul einige bedingte bereitstellen, primitive vorverarbeitung (beispielsweise die Ersetzung von einem einfachen Anführungszeichens ['] durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen). Genau wie (und ob) das scripting Modul verwendet diese Informationen hängen von dem Skriptmodul. Legen Sie diesen Parameter zu `NULL` Wenn der Host ein Trennzeichen nicht verwendet haben, um das Ende der Prozedur zu kennzeichnen.  
  
 `dwSourceContextCookie`  
 [in] Anwendungsdefinierten Wert, der für Debugzwecke verwendet wird.  
  
 `ulStartingLineNumber`  
 [in] Nullbasierter Wert, der angibt, in welcher Zeile die Analyse beginnen soll.  
  
 `dwFlags`  
 [in] Flags, die die Prozedur zugeordnet werden. Eine Kombination dieser Werte kann sein.  
  
|Konstante|Wert|Bedeutung|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Gibt an, dass der Code in `pstrCode` ist ein Ausdruck, den Rückgabewert der Prozedur darstellt.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Gibt an, dass die `this` Zeiger in den Bereich der Prozedur enthalten ist.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Gibt an, die den übergeordneten Elementen von der `this` Zeiger in den Bereich der Prozedur enthalten sind.|  
  
 `ppdisp`  
 [out] Gibt einen Dispatch-Wrapper zurück, in dem die Prozedur analysiert, die von dieser Methode ist die Standardmethode.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt. Das Skriptmodul wird zur Laufzeit-hinzufügen von Prozeduren, damit der Namespace nicht unterstützt.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul im nicht initialisierten oder geschlossenen Zustand ist).|  
|`OLESCRIPT_E_SYNTAX`|Ein nicht spezifizierter Syntaxfehler trat in der Prozedur.|  
|`S_FALSE`|Das Skriptmodul unterstützt keine Dispatch-Objekt; die `ppdisp`Parametersatz auf `NULL`.|  
  
## <a name="remarks"></a>Hinweise  
 Kein Skriptcode wird während dieses Aufrufs ausgewertet; stattdessen das Verfahren auf in eine Methode kompiliert wird `ppdisp` , in denen es kann aufgerufen werden vom Skript später erneut.  
  
 Diese Schnittstelle ist veraltet die `IActiveScriptParseProcedure` Schnittstelle. Die `IActiveScriptParseProcedure::ParseProcedureText` Methode ist vergleichbar mit dieser Methode, aber sie können den Namen der Prozedur angegeben werden. In allen Fällen `IActiveScriptParseProcedure::ParseProcedureText` verwendet werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParseProcedureOld-Schnittstelle](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)