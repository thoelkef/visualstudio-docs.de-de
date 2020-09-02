---
title: 'Idebugfield:: getContainer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f6c5b0cb1b14ac7cc34e284e2d073fafed9b20e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547129"
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ruft den Container eines Felds ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetContainer(   
   IDebugContainerField** ppContainerField  
);  
```  
  
```csharp  
int GetContainer(  
   out IDebugContainerField ppContainerField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppContainerField`  
 vorgenommen Gibt den Container zurück, wie durch die [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) -Schnittstelle dargestellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn dieses Feld keinen Container hat, ist der zurückgegebene `ppContainerField` ein NULL-Wert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
