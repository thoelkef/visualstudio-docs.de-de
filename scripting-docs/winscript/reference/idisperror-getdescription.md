---
title: 'Idisperror:: GetDescription | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetDescription
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetDescription
ms.assetid: 04deaea6-0265-4e34-952e-634edba0e923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d1bb1c3516c2601707e1a0bcd69f4f8409514fe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573145"
---
# <a name="idisperrorgetdescription"></a>IDispError::GetDescription
Gibt eine Textbeschreibung des Fehlers zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrDescription`  
 vorgenommen Eine Zeichenfolge, die eine kurze Beschreibung des Fehlers enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Der Text wird in der durch den Gebiets Schema Bezeichner (LCID) angegebenen Sprache zurückgegeben, der für die Methode, die den Fehler gefunden hat, an `IDispatchEx::InvokeEx` übermittelt wurde.  
  
> [!NOTE]
> Diese Methode ist nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Idisperror-Schnittstelle](../../winscript/reference/idisperror-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)