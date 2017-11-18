---
title: IScriptEntry::SetSignature | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.SetSignature
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9ff480f8e5c3192a7e2b355d39825cc3a084370
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Legt die Typinformationen für ein `IScriptEntry` Function-Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pti`  
 [in] Die Typinformationen.  
  
 `iMethod`  
 [in] Der Index der Methode in der `ITypeInfo` Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Legen Sie Typinformationen mit `IScriptEntry::SetSignature` oder [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Typinformationen kann auch durch den Eintrag basierend auf der internen Funktion Darstellung generiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)