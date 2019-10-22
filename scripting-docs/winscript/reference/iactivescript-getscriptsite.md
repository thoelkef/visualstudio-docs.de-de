---
title: 'IActiveScript:: getscriptsite | Microsoft-Dokumentation'
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
ms.openlocfilehash: 567c7b5c1ead5388e6ec9c67d6ab6f9f580adf20
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575745"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Ruft das Site Objekt ab, das der Windows-Skript-Engine zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `iid`  
 in Der Bezeichner der angeforderten Schnittstelle.  
  
 `ppvSiteObject`  
 vorgenommen Adresse des Speicher Orts, der den Schnittstellen Zeiger auf das Standort Objekt des Hosts empfängt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_NOINTERFACE`|Die angegebene Schnittstelle wird nicht unterstützt.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`S_FALSE`|Es wurde keine Site festgelegt. der `ppvSiteObject`-Parameter ist auf `NULL` festgelegt.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)