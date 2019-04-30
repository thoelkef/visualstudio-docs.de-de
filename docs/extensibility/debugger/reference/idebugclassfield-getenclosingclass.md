---
title: IDebugClassField::GetEnclosingClass | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e6b2cfae694d0d95f70b2251efc66764df1b539
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922777"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Klasse, die diese Klasse umschließt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppClassField`  
 [out] Gibt eine [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt darstellt, der einschließenden Klasse. Gibt einen null-Wert zurück, wenn keine einschließenden Klasse vorhanden ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Klasse von diesem dargestellt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt ist eine geschachtelte Klasse, die `ppClassField` gibt Parameter ein `IDebugClassField` Objekt darstellt, der einschließenden Klasse. Angenommen, dieser Klassendefinition:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Aufrufen der `GetEnclosingClass` Methode für die `IDebugClassField` Objekt darstellt der `NestedClass` -Klasse zurückgegeben wird ein `IDebugClassField` Objekt, das die Klasse darstellt `RootClass`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
