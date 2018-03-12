---
title: IActiveScriptAuthor::AddScriptlet | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b21f906a73a313bf775683ba63738adb25af0007
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Fügt einen Code-Scriptlet als ein untergeordnetes Element der Stammebene `IScriptNode` Objekt. Auf dem Host ist der vollqualifizierte Name des Scriptlets nur zwei Ebenen zulässig.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszDefaultName`  
 [in] Die Adresse der Standardname des Scriptlets zugeordnet werden soll.  
  
 `pszCode`  
 [in] Die Adresse des Scriptlet-Texts.  
  
 `pszItemName`  
 [in] Der Pufferadresse des Bezeichners der obersten Ebene mit dem vollqualifizierten Scriptlet-Namen auf dem Host.  
  
 `pszSubItemName`  
 [in] Der Pufferadresse von der zweiten Ebene-Bezeichner, der den vollqualifizierten Scriptlet-Namen auf dem Host. Auf NULL festgelegt, wenn der Name nur eine Ebene aufweist.  
  
 `pszEventName`  
 [in] Die Adresse eines Puffers, der den Namen des Ereignisses enthält, für den dem Scriptlet ein Ereignishandler ist.  
  
 `pszDelimiter`  
 [in] Die Adresse des Trennzeichens zum Ende der Skriptblock. Wenn `pszCode` wird analysiert, die aus einem Stream des Texts, verwendet der Host in der Regel ein Trennzeichen (z. B. zwei einfache Anführungszeichen), um das Ende des Skriptblocks zu erkennen. Legen Sie diesen Parameter auf NULL, wenn ein Trennzeichen nicht das Ende des Skriptblocks markieren.  
  
 `dwCookie`  
 [in] Ein anwendungsdefinierten Wert, der verwendet wird, ein Hostobjekt Scriptlet zugeordnet werden soll.  
  
 `dwFlags`  
 [in] Nicht verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)