---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6ef6a04d263e322d408bb7d7c95da1929d89010c
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "62569318"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bestimmt, ob ein benutzerdefiniertes Attribut nach Namen vorhanden ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Gibt zurück, S_OK Wenn das benutzerdefinierte Attribut für dieses Feld definiert ist, andernfalls S_FALSE zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie zum Abrufen der Attribut-Bytes, die mit dem benutzerdefinierten Attribut für die [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
