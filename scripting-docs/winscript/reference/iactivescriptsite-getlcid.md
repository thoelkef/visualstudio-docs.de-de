---
title: IActiveScriptSite::GetLCID | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6ebcfec9764aae98f7d74ac98e0c88ecec7c4da
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155510"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Ruft die Gebietsschema-ID, die Benutzeroberfläche des Hosts zugeordnet. Die Skript-Engine verwendet die ID, um sicherzustellen, dass die Zeichenfolgen und andere Elemente der Benutzeroberfläche von der Engine generierten in der entsprechenden Sprache angezeigt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `plcid`  
 [out] Die Adresse einer Variablen, die den Gebietsschemabezeichner für die Elemente der Benutzeroberfläche angezeigt, die von der Skript-Engine empfängt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_NOTIMPL`|Diese Methode ist nicht implementiert. Verwenden Sie das System definierten Gebietsschema.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn diese Methode zurückgibt `E_NOTIMPL`, der vom System definierte Gebietsschemabezeichner sollte verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)