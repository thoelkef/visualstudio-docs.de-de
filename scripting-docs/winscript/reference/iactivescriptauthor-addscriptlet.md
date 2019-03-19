---
title: IActiveScriptAuthor::AddScriptlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64df7bd4c0d0dde303cdc15d7111688d14c7dc49
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146980"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Fügt einen Code-Scriptlet als untergeordnetes Element der Stammebene `IScriptNode` Objekt. Auf dem Host ist der vollqualifizierte Name des Scriptlets nur zwei Ebenen zulässig.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
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
 [in] Die Pufferadresse des Bezeichners der obersten Ebene mit dem vollständig qualifizierten Scriptlet-Namen auf dem Host.  
  
 `pszSubItemName`  
 [in] Die Pufferadresse der Bezeichner der zweiten Ebene mit dem vollständig qualifizierten Scriptlet-Namen auf dem Host. Auf NULL festgelegt, wenn der Name nur eine Ebene enthält.  
  
 `pszEventName`  
 [in] Die Adresse eines Puffers, der den Ereignisnamen enthält, für den das Scriptlet ein Ereignishandler ist.  
  
 `pszDelimiter`  
 [in] Die Adresse des Trennzeichens Ende-des-Skript-Block. Wenn `pszCode` wird analysiert, die aus einem Stream des Texts, verwendet der Host in der Regel ein Trennzeichen (z. B. zwei einfache Anführungszeichen), um das Ende des Skriptblocks zu erkennen. Legen Sie diesen Parameter auf NULL, wenn ein Trennzeichen nicht das Ende des Skriptblocks markiert.  
  
 `dwCookie`  
 [in] Eine Anwendung definierte Wert, der verwendet wird, ein Hostobjekt für das Scriptlet zugeordnet werden soll.  
  
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