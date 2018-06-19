---
title: IActiveScriptAuthor::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 13e81d96ae817b2117f12cb56fd59759f4c2b849
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645510"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Skripttext analysiert und fügt Text an das Modul authoring Skript erstellt ein `IScriptEntry` Objekt, das den Skriptblock entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 [in] Der Skripttext analysiert.  
  
 `pszItemName`  
 [in] Der Pufferadresse, die der Elementname, die den Skriptblock zugeordneten enthält.  
  
 `pszDelimiter`  
 [in] Die Adresse des Trennzeichens zum Ende der Skriptblock. Wenn `pszCode` wird analysiert, die aus einem Stream des Texts, verwendet der Host in der Regel ein Trennzeichen (z. B. zwei einfache Anführungszeichen), um das Ende des Skriptblocks zu erkennen. Legen Sie diesen Parameter auf NULL, wenn es keine Trennzeichen ist, das das Ende der Skriptblock zu identifizieren.  
  
 `dwCookie`  
 [in] Eine anwendungsdefinierte-Wert, der mit dem neuen anfallen `IScriptEntry` Objekt.  
  
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