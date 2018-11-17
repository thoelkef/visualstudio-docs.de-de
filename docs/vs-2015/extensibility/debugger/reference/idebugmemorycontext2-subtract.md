---
title: IDebugMemoryContext2::Subtract | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 70ed92b6098a736baf3bfa927a368f38a9ba01a7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721604"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Subtrahiert den angegebenen Wert aus dem aktuellen Kontext aus, und gibt Sie einen neuen Kontext zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwCount`  
 [in] Die Anzahl der Bytes von Arbeitsspeicher zu verringern.  
  
 `ppMemCxt`  
 [out] Gibt eine neue [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Arbeitsspeicher-Kontext ist eine Adresse an, damit subtrahiert einen Wert aus einer Adresse generiert eine neue Adresse, die eine neue Kontextschnittstelle erforderlich sind.  
  
 Diese Methode muss immer einen neuen Kontext, erzeugen, auch wenn die resultierende Adresse außerhalb des Speicherbereichs, der diesem Kontext zugeordnet ist. Die einzige Ausnahme hierbei ist, wenn kein Arbeitsspeicher kann, für den neuen Kontext belegt werden oder `ppMemCxt` ist ein null-Wert (der ein Fehler ist).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

