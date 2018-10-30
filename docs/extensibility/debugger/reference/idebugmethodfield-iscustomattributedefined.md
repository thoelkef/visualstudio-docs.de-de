---
title: IDebugMethodField::IsCustomAttributeDefined | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d2481c014c149e51c4c9ee3ff837a65e040b7e8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882267"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Bestimmt, ob ein bestimmtes benutzerdefiniertes Attribut definiert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszCustomAttributeName`  
 [in] Eine Zeichenfolge, die mit dem Namen des zu suchenden benutzerdefinierten Attributs.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt zurück, S_OK Wenn das benutzerdefinierte Attribut für diese Methode definiert ist, andernfalls S_FALSE zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)