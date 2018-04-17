---
title: IEEVisualizerDataProvider::CanSetObjectForVisualizer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer method
ms.assetid: 70fd3c6f-2f82-43a3-993b-c1dc8aa080bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8848fd5628fbbb7e0e642de2389d6b98375fa6f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ieevisualizerdataprovidercansetobjectforvisualizer"></a>IEEVisualizerDataProvider::CanSetObjectForVisualizer
Diese Methode bestimmt, ob die Schnellansicht das Datenobjekt, das sie darstellt aktualisiert werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CanSetObjectForVisualizer(  
   BOOL* b  
);  
```  
  
```csharp  
int CanSetObjectForVisualizer(  
   out int b  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `b`  
 [out] Ungleich Null (`TRUE`) Wenn das Objekt, für die Schnellansicht aktualisiert werden kann, 0 (null) (`FALSE`), wenn dies nicht möglich.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Objekt möglicherweise nicht geändert werden, wenn sie nur-Lese Speicher, z. B. gebunden ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)