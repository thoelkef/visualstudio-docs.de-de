---
title: IDebugTypeFieldBuilder::CreatePointerToType | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CreatePointerToType
- IDebugTypeFieldBuilder::CreatePointerToType
ms.assetid: 73966e8a-b643-43e0-9b4e-0aa4b402ebbe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 611534843fd02cfd35fe3707917c6399c893db60
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910030"
---
# <a name="idebugtypefieldbuildercreatepointertotype"></a>IDebugTypeFieldBuilder::CreatePointerToType
Erstellt einen Zeiger auf den angegebenen Typ.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreatePointerToType(  
   IDebugField*  pTypeField,  
   IDebugField** pPtrToTypeField  
);  
```  
  
```csharp  
int CreatePointerToType(  
   IDebugField     pTypeField,  
   out IDebugField pPtrToTypeField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pTypeField`  
 [in] Typ, um zu zeigen. Es wird dargestellt, durch die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle.  
  
 `pPtrToTypeField`  
 [out] Gibt zurück, den Zeiger von einem neuen dargestellt **IDebugField** Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)