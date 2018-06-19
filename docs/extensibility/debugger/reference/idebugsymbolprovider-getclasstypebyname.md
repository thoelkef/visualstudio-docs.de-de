---
title: IDebugSymbolProvider::GetClassTypeByName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetClassTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetClassTypeByName method
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b972885a8999ac688ade380fbe9601d4274d205e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118582"
---
# <a name="idebugsymbolprovidergetclasstypebyname"></a>IDebugSymbolProvider::GetClassTypeByName
Diese Methode ruft die Klasse Feldtyp, die einen vollqualifizierten Klassennamen darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetClassTypeByName(   
   LPCOLESTR          pszClassName,  
   NAME_MATCH         nameMatch,  
   IDebugClassField** ppField  
);  
```  
  
```csharp  
int GetClassTypeByName(  
   string               pszClassName,   
   NAME_MATCH           nameMatch,   
   out IDebugClassField ppField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszClassName`  
 [in] Der Klassenname.  
  
 `nameMatch`  
 [in] Wählt den Typ der Übereinstimmung, z. B. Groß-/Kleinschreibung beachtet. Ein Wert aus der [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) Enumeration.  
  
 `ppField`  
 [out] Gibt den Klassentyp, dargestellt durch die [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Schnittstelle.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)