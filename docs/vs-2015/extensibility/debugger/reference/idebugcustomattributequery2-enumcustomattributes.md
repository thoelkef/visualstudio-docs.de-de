---
title: IDebugCustomAttributeQuery2::EnumCustomAttributes | Microsoft-Dokumentation
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
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c516d85a11e6d4e85cf86cf56f740e2f2bf7cf84
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511065"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugCustomAttributeQuery2::EnumCustomAttributes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes).  
  
Ruft einen Enumerator für alle benutzerdefinierten Attribute, die an dieses Feld angefügt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumCustomAttributes(   
   IEnumDebugCustomAttributes** ppEnum  
);  
```  
  
```csharp  
int EnumCustomAttributes(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) Objekt, das die Liste der benutzerdefinierten Attribute darstellt; andernfalls einen null-Wert, wenn keine benutzerdefinierten Attribute vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück, oder S_FALSE zurück, wenn keine benutzerdefinierten Attribute für dieses Feld vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben;  
  
## <a name="remarks"></a>Hinweise  
 Ein Feld kann mehrere benutzerdefinierte Attribute aufweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

