---
title: 'Iactivescriptauthor:: getinfofromcontext | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b8b9ad4677d580d495c72866be57712476d6a9c7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985326"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Gibt Typinformationen und Anker Positionen für ein bestimmtes Zeichen in einem Codeblock zurück. Dies stellt Informationen für Member-IntelliSense, globale Listen und Parameter Tipps bereit.  
  
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
 in Die Adresse der Codeblock-Zeichenfolge, die zum Generieren der Informationsergebnisse verwendet wird.  
  
 `cchCode`  
 in Die Länge des Code Blocks.  
  
 `ichCurrentPosition`  
 in Die Position des Zeichens relativ zum Anfang des Blocks.  
  
 `dwListTypesRequested`  
 in Die angeforderten Listen Typen. Kann eine Kombination der folgenden Werte sein:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Keine Liste.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Mitgliederliste.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Enum-Liste.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Ruft die Methoden Parameterliste auf.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Globale Liste.|  
  
 Der SCRIPT_CMPL_GLOBALLIST Typ wird als Standard Vervollständigungs Element behandelt, das mithilfe des OR-Operators mit anderen Vervollständigungs Elementen kombiniert werden kann. Die Skript Erstellungs-Engine versucht zunächst, Typinformationen für andere Vervollständigungs Listenelemente aufzufüllen. Wenn dies nicht möglich ist, füllt die Engine SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 vorgenommen Der Typ der angegebenen Liste.  
  
 `pichListAnchorPosition`  
 vorgenommen Der Start Index des Kontexts, der die aktuelle Position enthält. Der Start Index ist relativ zum Anfang des Blocks.  
  
 Dies wird nur aufgefüllt, wenn `dwListTypesRequested` SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST oder SCRIPT_CMPL_GLOBALLIST enthält. Bei anderen angeforderten Listen Typen ist das Ergebnis nicht definiert.  
  
 `pichFuncAnchorPosition`  
 vorgenommen Der Start Index des Funktions Aufrufes, der die aktuelle Position enthält. Der Start Index ist relativ zum Anfang des Blocks.  
  
 Dies wird nur aufgefüllt, wenn der Kontext, der die aktuelle Position enthält, ein Funktions Aufrufwert ist, und wenn `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST enthält. Andernfalls ist das Ergebnis nicht definiert.  
  
 `pmemid`  
 vorgenommen Die Mitgliedsnummer der Funktion, wie von einem Typ im `IProvideMultipleClassInfo``ppunk` out-Parameter definiert.  
  
 Dies wird nur aufgefüllt, wenn `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST enthält.  
  
 `piCurrentParameter`  
 vorgenommen Der Index des Parameters, der die aktuelle Position enthält. Wenn die aktuelle Position den Funktionsnamen hat, wird-1 zurückgegeben.  
  
 Der `piCurrentParameter` Wert wird nur aufgefüllt, wenn `dwListTypesRequested` SCRIPT_CMPL_PARAMLIST enthält.  
  
 `ppunk`  
 Die Typinformationen, die in Form eines `IProvideMultipleClassInfo` Objekts bereitgestellt werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Iprovidemultipleclassinfo-Schnittstelle](/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)   
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)