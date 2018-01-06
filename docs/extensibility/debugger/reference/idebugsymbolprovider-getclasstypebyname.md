---
title: IDebugSymbolProvider::GetClassTypeByName | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugSymbolProvider::GetClassTypeByName
helpviewer_keywords: IDebugSymbolProvider::GetClassTypeByName method
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4af89a2086e92c01aa677ddcda4a22e6f5e40098
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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