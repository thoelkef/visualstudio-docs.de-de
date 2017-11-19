---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthorProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9c4a1ba03a8498dbaa857dc5dbabba8914e54a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analysiert eine Code-Prozedur, die Code-Prozedur Text an das Modul authoring Skript hinzugefügt und erstellt ein `IScriptEntry` Objekt, das die Prozedur Code entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszCode`  
 [in] Der Skripttext analysiert.  
  
 `pszFormalParams`  
 [in] Die Adresse der formale Parameternamen für die Prozedur. Die Parameternamen müssen durch die entsprechenden Trennzeichen für das Datenbankmodul authoring Skript getrennt werden. Die Namen sollten nicht in Klammern eingeschlossen werden.  
  
 `pszProcedureName`  
 [in] Die Adresse der den Namen der Prozedur, die analysiert werden.  
  
 `pszItemName`  
 [in] Zugeordneten Puffer-Adressen, die den Namen des Elements enthält die `IScriptEntry` Objekt.  
  
 `pszDelimiter`  
 [in] Die Adresse des Trennzeichens zum Ende der Skriptblock. Wenn `pszCode` wird analysiert, die aus einem Stream des Texts, verwendet der Host in der Regel ein Trennzeichen (z. B. zwei einfache Anführungszeichen), um das Ende des Skriptblocks zu erkennen. Legen Sie diesen Parameter auf NULL, wenn es keine Trennzeichen ist, das das Ende des Skriptblocks zu markieren.  
  
 `dwCookie`  
 [in] Eine anwendungsdefinierte-Wert, der mit dem neuen anfallen `IScriptEntry` Objekt.  
  
 `dwFlags`  
 [in] Nicht verwendet.  
  
 `pdispFor`  
 [in] Nicht verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Die aktuelle [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Modul implementiert diese Methode nicht.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthorProcedure-Schnittstelle](../../winscript/reference/iactivescriptauthorprocedure-interface.md)