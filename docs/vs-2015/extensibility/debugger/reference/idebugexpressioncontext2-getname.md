---
title: IDebugExpressionContext2::GetName | Microsoft-Dokumentation
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
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 62faff603e60340063eb6bd8f0eb60ad82c839c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514031"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugExpressionContext2::GetName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpressioncontext2-getname).  
  
Ruft den Namen des dem Auswertungskontext ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrName`  
 [out] Gibt den Namen des dem Auswertungskontext zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Name ist die Beschreibung dieses Kontexts für die Auswertung. Es ist in der Regel etwas, das von einer ausdrucksauswertung analysiert werden können, die auf diese genaue Evaluierungskontext verweist. Beispielsweise ist in C++ der Name wie folgt:  
  
```  
"{ function-name, source-file-name, module-file-name }"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)

