---
title: IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetInfoFromContext
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27c13dbe51bb1150554275b5fbeacd00be2e445f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Gibt geben Informationen und Anker Positionen für ein angegebenes Zeichen in einem Code-Block. Dies bietet Informationen für Member, IntelliSense, globalen Listen und parametertipps.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszCode`  
 [in] Die Adresse der Code-Block Zeichenfolge verwendet, um die Ergebnisse Informationen zu generieren.  
  
 `cchCode`  
 [in] Die Länge des Codeblocks.  
  
 `ichCurrentPosition`  
 [in] Das Zeichen Position relativ zum Start des Blocks.  
  
 `dwListTypesRequested`  
 [in] Die Listentypen angefordert. Eine Kombination der folgenden Werte ist möglich:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Keine Liste.|  
|SCRIPT_CMPL_MEMBERLIST|0 x 0001|Liste der Member.|  
|SCRIPT_CMPL_ENUMLIST|0 x 0002|Enum-Liste.|  
|SCRIPT_CMPL_PARAMLIST|0 x 0004|Rufen Sie die Parameterliste der Methode.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Globale Liste.|  
  
 Der SCRIPT_CMPL_GLOBALLIST-Typ wird als ein Standardelement für den Abschluss behandelt, die durch andere Abschluss Elemente mit dem OR-Operator kombiniert werden können. Das Skript erstellen das Modul zuerst versucht, die Typinformationen für den anderen Elementen in Vervollständigungslisten aufzufüllen. Wenn dies fehlschlägt, wird das Modul für SCRIPT_CMPL_GLOBALLIST aufgefüllt.  
  
 `pdwListTypesProvided`  
 [out] Der Typ der angezeigten Liste.  
  
 `pichListAnchorPosition`  
 [out] Der Startindex des Kontexts, die die aktuelle Position enthält. Der Startindex ist relativ zum Start des Blocks.  
  
 Dieses Feld wird aufgefüllt, nur wenn `dwListTypesRequested` SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST oder SCRIPT_CMPL_GLOBALLIST enthält. Für andere Typen angeforderten Liste ist das Ergebnis nicht definiert.  
  
 `pichFuncAnchorPosition`  
 [out] Der Startindex des Funktionsaufrufs, der die aktuelle Position enthält. Der Startindex ist relativ zum Start des Blocks.  
  
 Dies wird aufgefüllt, nur, wenn der Kontext, die aktuelle Position enthält, einen Funktionsaufruf ist, und `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST enthält. Andernfalls ist das Ergebnis nicht definiert.  
  
 `pmemid`  
 [out] Der Wert der Funktion an, gemäß der Definition von einem Typ in der `IProvideMultipleClassInfo``ppunk` out-Parameter.  
  
 Dieses Feld wird aufgefüllt, nur wenn `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST enthält.  
  
 `piCurrentParameter`  
 [out] Der Index des Parameters, der die aktuelle Position enthält. Wenn die aktuelle Position auf den Namen der Funktion ist, wird-1 zurückgegeben.  
  
 Die `piCurrentParameter` Wert aufgefüllt wird nur dann, wenn `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST enthält.  
  
 `ppunk`  
 Die Typinformationen, die in Form von bereitgestellt wird ein `IProvideMultipleClassInfo` Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IProvideMultipleClassInfo-Schnittstelle](https://msdn.microsoft.com/library/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo.aspx)   
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)