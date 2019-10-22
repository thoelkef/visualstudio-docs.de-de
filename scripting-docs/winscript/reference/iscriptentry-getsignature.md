---
title: 'Iscriptentry:: GetSignature | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7b07ac64ce7e427a793f0af0db9a7905441d39b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575417"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Gibt Typinformationen für ein `IScriptEntry` Funktions Objekt zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppti`  
 vorgenommen Typinformationen, die diesem `IScriptEntry` Funktions Objekt zugeordnet sind.  
  
 `piMethod`  
 vorgenommen Der Methoden Index im `ITypeInfo`-Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Sie legen die Typinformationen mithilfe von [iscriptentry:: SetSignature](../../winscript/reference/iscriptentry-setsignature.md) oder [iscriptnode:: kreatechildhandler](../../winscript/reference/iscriptnode-createchildhandler.md)fest. Typinformationen können auch durch den Eintrag basierend auf der internen Funktions Darstellung generiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)