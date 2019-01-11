---
title: IActiveScriptAuthor::GetInfoFromContext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d32e2864f42fa9a2bfc30cfe83da7d4e021dfd0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088867"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Gibt geben Informationen und Positionen der Anker für ein angegebenes Zeichen in einem Codeblock. Dies bietet Informationen für Mitglied, IntelliSense, globale Listen und parametertipps.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
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
 [in] Die Adresse der Zeichenfolge der Block verwendet, um die Ergebnisse der Informationen zu generieren.  
  
 `cchCode`  
 [in] Die Länge des Codeblocks.  
  
 `ichCurrentPosition`  
 [in] Position relativ zum Start des Blocks des Zeichens.  
  
 `dwListTypesRequested`  
 [in] Die angeforderte Listentypen. Eine Kombination der folgenden Werte sind möglich:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Keine Liste.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Memberliste aus.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Enum-Liste.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Rufen Sie die Parameterliste der Methode.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Globale Liste.|  
  
 Der SCRIPT_CMPL_GLOBALLIST-Typ wird als ein vervollständigungselement Standard behandelt, die andere Elemente der Vervollständigung mit der OR-Operator kombiniert werden können. Das Skript mit dem authoring-Engine zunächst versucht, die Typinformationen für den anderen Elementen in Vervollständigungslisten auffüllen. Wenn dies fehlschlägt, füllt die Engine für SCRIPT_CMPL_GLOBALLIST auf.  
  
 `pdwListTypesProvided`  
 [out] Der Typ der angegebenen Liste.  
  
 `pichListAnchorPosition`  
 [out] Der Startindex des Kontexts, die die aktuelle Position enthält. Der Startindex ist relativ zum Start des Blocks.  
  
 Dies wird gefüllt, nur, wenn `dwListTypesRequested` SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST oder SCRIPT_CMPL_GLOBALLIST enthält. Für andere Typen angeforderten Liste ist das Ergebnis nicht definiert.  
  
 `pichFuncAnchorPosition`  
 [out] Der Startindex des Funktionsaufrufs, der die aktuelle Position enthält. Der Startindex ist relativ zum Start des Blocks.  
  
 Dies wird gefüllt, nur, wenn der Kontext, die aktuelle Position enthält, auf ein Funktionsaufruf ist, und wenn `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST enthält. Andernfalls ist das Ergebnis nicht definiert.  
  
 `pmemid`  
 [out] Der Wert der Funktion gemäß der von einem Typ in der `IProvideMultipleClassInfo``ppunk` out-Parameter.  
  
 Dies wird gefüllt, nur, wenn `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST enthält.  
  
 `piCurrentParameter`  
 [out] Der Index des Parameters, der die aktuelle Position enthält. Wenn die aktuelle Position auf den Namen der Funktion ist, wird-1 zurückgegeben.  
  
 Die `piCurrentParameter` Wert aufgefüllt wird nur dann, wenn `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST enthält.  
  
 `ppunk`  
 Der von Typinformationen in Form von bereitgestellt wird ein `IProvideMultipleClassInfo` Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IProvideMultipleClassInfo-Schnittstelle](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)   
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)