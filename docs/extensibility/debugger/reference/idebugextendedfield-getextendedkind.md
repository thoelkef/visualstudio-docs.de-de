---
title: IDebugExtendedField::GetExtendedKind | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExtendedField::GetExtendedKind
- GetExtendedKind
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5e1be1da0ca207f5bc030bf5de72efdb0d24ea8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897601"
---
# <a name="idebugextendedfieldgetextendedkind"></a>IDebugExtendedField::GetExtendedKind
Ruft die Art des angegebenen erweiterten Feldeigenschaften ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetExtendedKind(  
   FIELD_KIND_EX* pdwKind  
);  
```  
  
```csharp  
int GetExtendedKind(  
   ref enum_FIELD_KIND_EX pdwKind  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwKind`  
 [in, out] Wert aus der [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) Enumeration, die die Art des Felds definiert.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)