---
title: IDebugCustomAttribute::GetName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15e02cdd0f1f3e601a37d144c9476877646674c4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872953"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Namen des benutzerdefinierten Attributs.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

