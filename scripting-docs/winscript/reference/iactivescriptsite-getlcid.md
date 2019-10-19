---
title: 'Iactivescriptsite:: GetLcid | Microsoft-Dokumentation'
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
ms.openlocfilehash: 913ca23ac687fdd080a778afb1dcba2e4dcdd6b8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570739"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Ruft den Gebiets Schema Bezeichner ab, der der Benutzeroberfläche des Hosts zugeordnet ist. Die Skript-Engine verwendet den Bezeichner, um sicherzustellen, dass Fehler Zeichenfolgen und andere von der Engine generierte Benutzeroberflächen Elemente in der entsprechenden Sprache angezeigt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `plcid`  
 vorgenommen Adresse einer Variablen, die den Gebiets Schema Bezeichner für Benutzeroberflächen Elemente empfängt, die von der Skript-Engine angezeigt werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_NOTIMPL`|Diese Methode ist nicht implementiert. Verwenden Sie das vom System definierte Gebiets Schema.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn diese Methode `E_NOTIMPL` zurückgibt, sollte der vom System definierte Gebiets Schema Bezeichner verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)