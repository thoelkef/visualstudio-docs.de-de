---
title: IDebugCustomAttribute::GetName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11a4b986799cf03221b4af077fc3e1e5809c4137
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866479"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Ruft den Namen des benutzerdefinierten Attributs.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bstrName`  
 [out] Gibt eine Zeichenfolge, die mit dem Namen des benutzerdefinierten Attributs.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die von dieser Methode zurückgegebene benannte entspricht dem Namen der Klasse verwendet, um das Attribut zu deklarieren. Dies möglicherweise nicht genau auf den Namen der benutzerdefinierten Attributklasse selbst entsprechen, wie in c# können das Suffix "Attribute" aus einem benutzerdefinierten Attributnamen gelöscht werden soll, wenn er in einer Deklaration verwendet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)