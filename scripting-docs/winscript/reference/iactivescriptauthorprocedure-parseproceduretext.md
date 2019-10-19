---
title: Iactivescriptauthorprocedure::P arabproceduretext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11a34843f30274ec78f1652c5ed5cd4dbcf2884a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572814"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analysiert eine Code Prozedur, fügt der Skript Erstellungs-Engine den Text der Code Prozedur hinzu und erstellt ein `IScriptEntry`-Objekt, das der Code Prozedur entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
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
 in Der Skript Text, der analysiert werden soll.  
  
 `pszFormalParams`  
 in Die Adresse der formalen Parameternamen für die Prozedur. Die Parameternamen müssen durch die entsprechenden Trennzeichen für die Skript Erstellungs-Engine getrennt werden. Die Namen dürfen nicht in die Klammern eingeschlossen werden.  
  
 `pszProcedureName`  
 in Die Adresse des zu erteilenden Prozedur namens.  
  
 `pszItemName`  
 in Die Puffer Adresse, die den dem `IScriptEntry` Objekt zugeordneten Elementnamen enthält.  
  
 `pszDelimiter`  
 in Die Adresse des Trenn Zeichens für das Ende des Skript Blocks. Wenn `pszCode` aus einem Stream von Text analysiert wird, verwendet der Host normalerweise ein Trennzeichen (z. b. zwei einfache Anführungszeichen), um das Ende des Skript Blocks zu erkennen. Legen Sie diesen Parameter auf NULL fest, wenn es kein Trennzeichen gibt, um das Ende des Skript Blocks zu markieren.  
  
 `dwCookie`  
 in Ein von der Anwendung definierter Wert, der mit dem neuen `IScriptEntry`-Objekt verknüpft ist.  
  
 `dwFlags`  
 in Nicht verwendet.  
  
 `pdispFor`  
 in Nicht verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Die aktuelle [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Engine implementiert diese Methode nicht.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthorProcedure-Schnittstelle](../../winscript/reference/iactivescriptauthorprocedure-interface.md)