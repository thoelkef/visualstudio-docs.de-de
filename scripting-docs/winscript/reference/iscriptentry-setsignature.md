---
title: 'Iscriptentry:: SetSignature | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e381e642462fe56e661de9da0d8974dc7bf18b18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575339"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Legt Typinformationen für ein `IScriptEntry` Funktions Objekt fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pti`  
 in Die Typinformationen.  
  
 `iMethod`  
 in Der Methoden Index im `ITypeInfo`-Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Sie legen Typinformationen mithilfe von `IScriptEntry::SetSignature` oder [iscriptnode:: kreatechildhandler](../../winscript/reference/iscriptnode-createchildhandler.md)fest. Typinformationen können auch durch den Eintrag basierend auf der internen Funktions Darstellung generiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)