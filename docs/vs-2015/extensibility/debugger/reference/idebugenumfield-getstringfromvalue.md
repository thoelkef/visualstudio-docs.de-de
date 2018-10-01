---
title: IDebugEnumField::GetStringFromValue | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38dbd88ea8b84c64b277daf5b77970fa127d82fd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512359"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugEnumField::GetStringFromValue](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugenumfield-getstringfromvalue).  
  
Diese Methode ruft den Namen der Enumerationskonstante erhält den Wert ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```csharp  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `value`  
 [in] Der Wert für das der Name der Enumeration Konstanten abgerufen werden soll.  
  
 `pbstrValue`  
 [out] Der Name der Enumerationskonstante zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` , wenn der Wert keinen zugeordneten Namen hat, oder gibt einen Fehlercode zurück.  
  
## <a name="remarks"></a>Hinweise  
 Ist mehr als einen Namen, die den gleichen Wert zugeordnet, wird der Vorname in der Enumeration definierte zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)

