---
title: IDebugCustomAttribute::GetAttributeTypeField | Microsoft-Dokumentation
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
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 93d1252128d7af95e40b7a3e7a5ae91c31e78af8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511115"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugCustomAttribute::GetAttributeTypeField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcustomattribute-getattributetypefield).  
  
Ruft ab, der Typ des benutzerdefinierten Attributs-Klasse.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetAttributeTypeField(   
   IDebugClassField** ppCAType  
);  
```  
  
```csharp  
int GetAttributeTypeField(  
   out IDebugClassField ppCAType  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppCAType`  
 [out] Gibt die [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt, das die Klasse darstellt, von denen das benutzerdefinierte Attribut eine Instanz ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein benutzerdefiniertes Attribut ist immer eine Klasse. Diese Methode ermöglicht den Zugriff auf eine [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt, das diese Klasse beschreibt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

