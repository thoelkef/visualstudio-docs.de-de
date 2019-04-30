---
title: IDebugMemoryContext2::Subtract | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6bc84d1658fe71131f75825fa4b8b50d8aa9e31b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918764"
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
