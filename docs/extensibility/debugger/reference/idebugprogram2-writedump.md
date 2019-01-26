---
title: IDebugProgram2::WriteDump | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4fc77748e456a612130de4b8f814ea7ba491f22
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021844"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Schreibt einen Dump in eine Datei an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `DumpType`  
 [in] Ein Wert aus der [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) -Enumeration, der den Typ des Dumps, gibt an, z. B. "," short oder Long.  
  
 `pszDumpUrl`  
 [in] Die URL, die das Speichern des Abbilds angegeben. Dies ist normalerweise in Form von `file://c:\path\filename.ext`, aber eine beliebige gültige URL sein kann.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Programm Dump würde in der Regel enthalten, den aktuellen Stapelrahmen, der Stapel selbst, eine Liste der Threads, die auf das Programm, und möglicherweise Speicher, der die Anwendung besitzt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)