---
title: ISimpleConnectionPoint::Unadvise | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83fdf8f6a6e9378d328a9df61b1561a1ae747ae8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089264"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Beendet eine Advise-Verbindung, die zuvor über `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwCookie`  
 [in] Die Verbindung beendet wurde, der von zurückgegebene Token `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Advise-Verbindung beendet wird, zeigen Sie die Verbindung Aufrufe der `Release` Methode für den Zeiger, der gespeichert wurde, für die Verbindung während der `ISimpleConnectionPoint::Advise` Methode. Aufrufen kehrt das Ergebnis der `AddRef` , wurde ausgeführt, während die `ISimpleConnectionPoint::Advise` Wenn der Verbindungspunkt für der Advise-Senke aufruft `QueryInterface`.  
  
## <a name="see-also"></a>Siehe auch  
 [ISimpleConnectionPoint-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)