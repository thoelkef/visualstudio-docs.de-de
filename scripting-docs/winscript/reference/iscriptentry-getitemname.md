---
title: IScriptEntry::GetItemName | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptEntry.GetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetItemName
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cdbb293afc6f58f8d9d9c1fe27bae467fd36792c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetitemname"></a>IScriptEntry::GetItemName
Gibt zurück, der Name des Elements identifiziert eine `IScriptEntry` Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstr`  
 [out] Die Adresse eines Puffers, der den Namen des Elements enthält. Der Name des Elements wird vom Host zum Identifizieren des Eintrags verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Für `IScriptScriptlet` Objekte aufweist, legen Sie den Namen des Elements mit [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md). Für andere Schnittstellen, legen Sie den Namen des Elements mit [IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)