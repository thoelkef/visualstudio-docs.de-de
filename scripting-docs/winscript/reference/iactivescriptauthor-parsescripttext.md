---
title: Iactivescriptauthor::P arsescripttext | Microsoft-Dokumentation
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
ms.openlocfilehash: 90d5ab0fa700ed29b5fb37b1c48617cedec871b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576148"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analysiert Skript Text, fügt den Text der Skript Erstellungs-Engine hinzu und erstellt ein `IScriptEntry`-Objekt, das dem Skriptblock entspricht.  
  
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
 in Der Skript Text, der analysiert werden soll.  
  
 `pszItemName`  
 in Die Puffer Adresse, die den dem Skriptblock zugeordneten Elementnamen enthält.  
  
 `pszDelimiter`  
 in Die Adresse des Trenn Zeichens für das Ende des Skript Blocks. Wenn `pszCode` aus einem Stream von Text analysiert wird, verwendet der Host normalerweise ein Trennzeichen (z. b. zwei einfache Anführungszeichen), um das Ende des Skript Blocks zu erkennen. Legen Sie diesen Parameter auf NULL fest, wenn es kein Trennzeichen gibt, um das Ende des Skript Blocks zu identifizieren.  
  
 `dwCookie`  
 in Ein von der Anwendung definierter Wert, der mit dem neuen `IScriptEntry`-Objekt verknüpft ist.  
  
 `dwFlags`  
 in Nicht verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)