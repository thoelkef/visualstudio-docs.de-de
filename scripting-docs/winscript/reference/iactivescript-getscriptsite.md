---
title: IActiveScript::GetScriptSite | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b57c4282b7ec77eb4af2ffa983479ae77388e1c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935770"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Ruft das zugeordnete Windows-Skript-Engine-Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `iid`  
 [in] Der Bezeichner der angeforderten Schnittstelle.  
  
 `ppvSiteObject`  
 [out] Die Adresse des Speicherorts, die den Schnittstellenzeiger auf den Host Site-Objekt empfängt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_NOINTERFACE`|Die angegebene Schnittstelle wird nicht unterstützt.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`S_FALSE`|Keine Website wurde festgelegt wurde; die `ppvSiteObject` Parametersatz zu `NULL`.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)