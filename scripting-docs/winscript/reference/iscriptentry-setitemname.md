---
title: IScriptEntry::SetItemName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20af0975a4175d10b110ac5e3cef9e0055f4ce1b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097759"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Legt den Namen, der identifiziert eine `IScriptEntry` Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `psz`  
 [in] Die Adresse eines Puffers, der den Namen des Elements enthält. Der Name des Elements wird vom Host zum Identifizieren des Eintrags.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die Methode war nicht erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Für `IScriptEntry` Objekten, die Rückgabe dieser Methode `S_OK`.  
  
 Für `IScriptScriptlet` Objekte (die abgeleitet `IScriptEntry`), gibt diese Methode `E_FAIL`. Für `IScriptScriptlet` Objekten, die den Namen des Elements wird festgelegt, indem [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) und kann nicht geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)