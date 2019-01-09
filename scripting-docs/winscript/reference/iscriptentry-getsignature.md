---
title: IScriptEntry::GetSignature | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 245b5806006ad94740e09e23f881e26e071a3bc1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092728"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Gibt die Typinformationen für ein `IScriptEntry` Function-Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppti`  
 [out] Geben Sie Informationen, die zugeordneten `IScriptEntry` Function-Objekt.  
  
 `piMethod`  
 [out] Index der Methode in der `ITypeInfo` Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Legen Sie Typinformationen mit [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) oder [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Typinformationen kann auch durch den Eintrag, der basierend auf Ihrer Darstellung in der internen Funktion generiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)