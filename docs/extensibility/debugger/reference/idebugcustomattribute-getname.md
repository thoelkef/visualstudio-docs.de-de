---
title: IDebugCustomAttribute::GetName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8237fe3ad25baa912ee3a1eb84da533d788346cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Ruft den Namen des benutzerdefinierten Attributs ab.  
  
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
 [out] Gibt eine Zeichenfolge mit dem Namen des benutzerdefinierten Attributs.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die von dieser Methode zurückgegebene benannte entspricht dem Namen der Klasse verwendet, um das Attribut zu deklarieren. Dies möglicherweise nicht genau den Namen der benutzerdefinierten Attributklasse selbst entspricht c# können das Suffix "Attribute" aus benutzerdefiniertem Attributsnamen gelöscht werden, wenn er in einer Deklaration verwendet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)