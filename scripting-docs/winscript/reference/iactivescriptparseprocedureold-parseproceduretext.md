---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft-Dokumentation
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
ms.openlocfilehash: 8e521bbdcd8d7397c1c2dfb377fd9b41811499f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993214"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Die Prozedur angegebenen Code analysiert und fügt eine anonyme Prozedur auf den Namespace.  
  
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
 [in] Der Text der Prozedur, ausgewertet werden soll. Die Darstellung dieser Zeichenfolge hängt von der Skriptsprache ab.  
  
 `pstrFormalParams`  
 [in] Formale Parameternamen für die Prozedur. Die Parameternamen müssen mit den entsprechenden Trennzeichen für die Skript-Engine getrennt werden. Die Namen sollten nicht in Klammern eingeschlossen werden.  
  
 `pstrItemName`  
 [in] Der Name des benannten Elements, das den Kontext angibt, in dem die Prozedur ist, ausgewertet werden soll. Wenn dieser Parameter ist `NULL`, der Code im globalen Kontext des Skriptmoduls ausgewertet wird.  
  
 `punkContext`  
 [in] Das Context-Objekt. Dieses Objekt ist für die Verwendung in einer Debugumgebung reserviert, in der ein solcher Kontext möglicherweise vom Debugger bereitgestellt wird, um einen aktiven Laufzeitkontext darzustellen. Wenn dieser Parameter ist `NULL`, verwendet die Engine `pstrItemName` auf den Kontext zu identifizieren.  
  
 `pstrDelimiter`  
 [in] Das Ende der Prozedur Trennzeichen. Wenn `pstrCode` wird analysiert, die aus einem Stream von Text und einem Trennzeichen, der Host in der Regel verwendet, wie z. B. zwei Anführungszeichen ("), um das Ende der Prozedur erkennen einfache. Dieser Parameter gibt das Trennzeichen, das der Host verwendet, sodass dem Skriptmodul einige bedingte, bereitstellen, primitive vorverarbeitung (z. B., und Ersetzen Sie ein einfaches Anführungszeichen ['] durch zwei einfache Anführungszeichen für die Verwendung als Trennzeichen). Genau wie (und ob) die Skript-Engine-verwendet diese Informationen hängen von der Skript-Engine. Legen Sie diesen Parameter `NULL` Wenn der Host ein einzeln verwendetes Trennzeichen nicht verwendet haben, um das Ende der Prozedur markieren.  
  
 `dwSourceContextCookie`  
 [in] Anwendung definierter Wert, der zum Debuggen verwendet wird.  
  
 `ulStartingLineNumber`  
 [in] Nullbasierter Wert, der angibt, in welcher Zeile die Analyse beginnt.  
  
 `dwFlags`  
 [in] Flags, die mit der Prozedur. Eine Kombination der folgenden Werte kann sein.  
  
|Konstante|Wert|Bedeutung|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Gibt an, dass der Code in `pstrCode` ist ein Ausdruck, der den Rückgabewert der Prozedur darstellt.|  
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
|`E_NOTIMPL`|Diese Methode wird nicht unterstützt. Die Skript-Engine unterstützt keine Laufzeit-hinzufügen von Prozeduren auf den Namespace.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul im nicht initialisierten oder geschlossenen Zustand ist).|  
|`OLESCRIPT_E_SYNTAX`|Ein nicht spezifizierter Syntaxfehler trat in der Prozedur.|  
|`S_FALSE`|Die Skript-Engine unterstützt nicht die Dispatch-Objekt. die `ppdisp`Parametersatz zu `NULL`.|  
  
## <a name="remarks"></a>Hinweise  
 Kein Skriptcode wird während dieses Aufrufs ausgewertet; stattdessen das Verfahren bei in eine Methode kompiliert wird `ppdisp` , in dem er kann aufgerufen werden, durch das Skript später noch mal.  
  
 Diese Schnittstelle ist veraltet, zugunsten des der `IActiveScriptParseProcedure` Schnittstelle. Die `IActiveScriptParseProcedure::ParseProcedureText` Methode ist diese Methode ähnelt, aber sie können den Namen der Prozedur angegeben werden. In jedem Fall `IActiveScriptParseProcedure::ParseProcedureText` verwendet werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParseProcedureOld-Schnittstelle](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)