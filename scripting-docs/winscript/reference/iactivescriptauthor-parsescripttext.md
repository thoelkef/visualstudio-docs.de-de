---
title: IActiveScriptAuthor::ParseScriptText | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe6870f3b19c5727fdbea0418b8373b990cb671a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144718"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Skripttext analysiert und fügt den Text an das Skript-Engine-Erstellung erstellt eine `IScriptEntry` Objekt, das den Skriptblock entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszCode`  
 [in] Der Skripttext analysiert werden soll.  
  
 `pszItemName`  
 [in] Die Pufferadresse, die den Namen des zugeordneten des Skriptblocks enthält.  
  
 `pszDelimiter`  
 [in] Die Adresse des Trennzeichens Ende-des-Skript-Block. Wenn `pszCode` wird analysiert, die aus einem Stream des Texts, verwendet der Host in der Regel ein Trennzeichen (z. B. zwei einfache Anführungszeichen), um das Ende des Skriptblocks zu erkennen. Legen Sie diesen Parameter auf NULL, wenn es keine Trennzeichen ist, das das Ende der Skriptblock zu identifizieren.  
  
 `dwCookie`  
 [in] Einer der Anwendung definierter Wert, der mit dem neuen verknüpft ist `IScriptEntry` Objekt.  
  
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