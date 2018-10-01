---
title: IDebugClassField::EnumConstructors | Microsoft-Dokumentation
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
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f8b3db7989505c2921ca88090fe104ae547d7b0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514894"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugClassField::EnumConstructors](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugclassfield-enumconstructors).  
  
Erstellt einen Enumerator für die Konstruktoren für diese Klasse.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cMatch`  
 [in] Ein Wert aus der [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) -Enumeration, der den Typ der Konstruktoren verwenden, um die Enumeration angibt.  
  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der Konstruktoren darstellt. Gibt einen null-Wert zurück, wenn es keine Konstruktoren gibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück, oder gibt S_FALSE zurück, wenn es keine Konstruktoren gibt. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Jedes Element der Enumeration ist ein [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) Objekt, das eine Konstruktormethode beschreibt.  
  
 Die Liste der Konstruktoren umfasst in der Regel nicht die Standardkonstruktoren, die vom Compiler bereitgestellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)

