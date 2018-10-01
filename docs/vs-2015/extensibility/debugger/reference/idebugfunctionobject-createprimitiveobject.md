---
title: IDebugFunctionObject::CreatePrimitiveObject | Microsoft-Dokumentation
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
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 320930a86a58b51155b3f7400ea791135c321d95
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522719"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugFunctionObject::CreatePrimitiveObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject).  
  
Erstellt ein Datenobjekt mit primitiven, z. B. einer einfachen ganzen Zahl.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ot`  
 [in] Ein Wert aus der [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) Enumeration, die den Typ des primitiven Erstellung darstellt.  
  
 `ppObject`  
 [out] Gibt eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , das das neu erstellte Objekt darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie diese Methode zum Erstellen eines Objekts, das ein Primitiv-Objekt, die einen Parameter an die Funktion der darstellt durch dargestellt wird, wird die [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Schnittstelle. Wenn die Zeichenfolge des Ausdrucks "myString(5)" ist, würde z. B. diese Methode verwendet werden, erstellen Sie ein Objekt, das die ganze Zahl 5 darstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)

