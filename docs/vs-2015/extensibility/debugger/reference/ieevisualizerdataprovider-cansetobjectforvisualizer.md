---
title: 'Ieevisualizerdataprovider:: cansetobjectforvisualizer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer method
ms.assetid: 70fd3c6f-2f82-43a3-993b-c1dc8aa080bf
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af1569e315b2010ad734c8776bd8436110365c40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196168"
---
# <a name="ieevisualizerdataprovidercansetobjectforvisualizer"></a>IEEVisualizerDataProvider::CanSetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode bestimmt, ob für die Schnellansicht das Datenobjekt, das Sie darstellt, aktualisiert werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CanSetObjectForVisualizer(  
   BOOL* b  
);  
```  
  
```csharp  
int CanSetObjectForVisualizer(  
   out int b  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `b`  
 vorgenommen Ungleich NULL ( `TRUE` ), wenn das Objekt in der Schnellansicht aktualisiert werden kann, andernfalls NULL ( `FALSE` ).  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Objekt kann z. b. nicht geändert werden, wenn es an einen schreibgeschützten Speicher gebunden ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
