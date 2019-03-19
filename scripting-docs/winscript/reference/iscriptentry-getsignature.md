---
title: IScriptEntry::GetSignature | Microsoft-Dokumentation
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
ms.openlocfilehash: 70cc1939ae4eb1e3c58d31b3d42b7f1b4603ce9e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145303"
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