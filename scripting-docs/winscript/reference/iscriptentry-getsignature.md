---
title: IScriptEntry::GetSignature | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetSignature
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 062f069bb6a19c24f26a6a0bc6a9f4de2292d88f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Gibt Informationen zum Eingeben einer `IScriptEntry` Function-Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppti`  
 [out] Typinformationen zugeordnete `IScriptEntry` Function-Objekt.  
  
 `piMethod`  
 [out] Methode Index in die `ITypeInfo` Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Legen Sie Typinformationen mit [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) oder [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Typinformationen kann auch durch den Eintrag basierend auf der internen Funktion Darstellung generiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)