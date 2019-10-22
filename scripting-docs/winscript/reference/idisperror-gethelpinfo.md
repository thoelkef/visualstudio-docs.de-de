---
title: 'Idisperror:: gethelpinfo | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a84e57e97bb781ad3ea0be1ac6766fd94f6f5c30
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573136"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Gibt, sofern möglich, den Pfad der Hilfedatei und die Kontext-ID des Themas zurück, in dem der Fehler erläutert wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrFileName`  
 vorgenommen Zeichenfolge, die den voll qualifizierten Pfad der Hilfedatei enthält. Wenn keine Hilfedatei vorhanden ist oder ein Fehler auftritt, ist der Rückgabewert NULL.  
  
 `pdwContext`  
 vorgenommen Die Hilfe Kontext-ID für den Fehler. Wenn keine Hilfedatei vorhanden ist (wenn `pbstrFileName` NULL ist), hat dieser Parameter keine Bedeutung.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Ein Anbieter spezifischer Fehler ist aufgetreten.|  
|`E_INVALIDARG`|`pbstrFileName` oder `pdwContext` war NULL.|  
|`E_OUTOFMEMORY`|Der Anbieter konnte nicht genügend Arbeitsspeicher zuordnen, um den Hilfe Dateipfad zurückzugeben.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt, sofern möglich, den Pfad der Hilfedatei und die Kontext-ID des Themas zurück, das den Fehler erläutert.  
  
> [!NOTE]
> Diese Methode ist nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDispError-Schnittstelle](../../winscript/reference/idisperror-interface.md)