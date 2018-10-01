---
title: IDebugProgram2::GetDebugProperty | Microsoft-Dokumentation
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
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e92d0a20fb9639e3a969ff30a5b6b512019895a5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509099"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugProgram2::GetDebugProperty](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-getdebugproperty).  
  
Ruft die Anwendung die Eigenschaften ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppProperty`  
 [out] Gibt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt, das die Eigenschaften des Programms darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die von dieser Methode zurückgegebenen Eigenschaften sind spezifisch für die Anwendung. Wenn die Anwendung mehr als eine Eigenschaft zurückgeben muss die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) von dieser Methode zurückgegebene Objekt ist ein Container für zusätzliche Eigenschaften und Aufrufen der [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) Methode gibt ein Liste aller Eigenschaften.  
  
 Ein Programm kann verfügbar machen, beliebiger Anzahl und Art von zusätzlichen Eigenschaften, die über beschrieben werden, kann die `IDebugProperty2` Schnittstelle. Eine IDE möglicherweise die Eigenschaften der zusätzliche Anwendung über eine generische Eigenschaft-Browser-Benutzeroberfläche angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)

