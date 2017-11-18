---
title: IActiveScriptSite::GetLCID | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.GetLCID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6e128f5ac5de11b45af59c83750411c35e6efa7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Ruft die Gebietsschema-ID, die Benutzeroberfläche des Hosts zugeordnet. Das Skriptmodul verwendet den Bezeichner, um sicherzustellen, dass die Fehlerzeichenfolgen und andere Elemente der Benutzeroberfläche vom Modul generierten in der entsprechenden Sprache angezeigt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `plcid`  
 [out] Die Adresse einer Variablen, der den Gebietsschemabezeichner für die Elemente der Benutzeroberfläche angezeigt, die vom Skriptmodul empfängt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_NOTIMPL`|Diese Methode ist nicht implementiert. Verwenden Sie das System definierte Gebietsschema.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn diese Methode zurückgibt `E_NOTIMPL`, der vom System definierte Gebietsschemabezeichner sollte verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)