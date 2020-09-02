---
title: 'IDebugPortSupplier3:: canpersistports | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: edc989771b41cc4a5cc5b4710de4cbb5632873e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188185"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode bestimmt, ob der Port Lieferant Ports (durch das Schreiben auf den Datenträger) zwischen den Aufrufen des Debuggers beibehalten kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine.  
  
## <a name="return-value"></a>Rückgabewert  
 `S_OK` , wenn Ports persistent sein können, oder, `S_FALSE` um anzugeben, dass die Ports nicht persistent sein können.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der Port Lieferant Ports beibehalten kann, sollte er dies tun, wenn er zerstört wird, und ihn dann erneut laden, wenn er erneut instanziiert wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
