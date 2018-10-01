---
title: IDebugObject2::GetBackingFieldForProperty | Microsoft-Dokumentation
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
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b29b6eb411c511612b60faf271d23decd7370c12
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515628"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugObject2::GetBackingFieldForProperty](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty).  
  
Ruft ab, das Feld oder eine Variable (sofern vorhanden), die von diesem Objekt dargestellte Eigenschaft sichern.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppObject`  
 [out] Ein [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) Objekt, das das dahinter liegende Feld beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) Objekt stellt verwalteten Code Klasseneigenschaft, d. h. eine Methode mit einer Get bzw. set-Accessor. Diese Eigenschaften erfordern in der Regel eine Variable, die den Wert, der bearbeitet werden, durch die Eigenschaft enthalten. Diese Variable wird als das dahinter liegende Feld bezeichnet. Liegt keine dahinter liegende Feld für das Objekt, dann stellen Sie sicher auf einen Nullwert zurückgibt: Einige Aufrufer kann keine Achten Sie darauf, den Rückgabewert, aber sehen Sie sich stattdessen um festzustellen, ob ein null-Wert, in zurückgegeben wurde `ppObject`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)

