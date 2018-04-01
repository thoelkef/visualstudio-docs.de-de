---
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 40fcd345a2a07a0ebdcf9e984b060cc81e946fc3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Schreibt einen Dump in eine Datei.  
  
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
 [in] Ein Wert aus der [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) -Enumeration, der den Typ des Abbilds, gibt an, z. B. "," short "oder" Long-Wert.  
  
 `pszDumpUrl`  
 [in] Die URL für das Speicherabbild zu schreiben. Dies ist normalerweise in Form von `file://c:\path\filename.ext`, aber gültige URL sein kann.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Programm Speicherabbild würde in der Regel enthalten, den aktuellen Stapelrahmen, der Stapel selbst, eine Liste der Threads im Programm und möglicherweise Speicher, der die Anwendung besitzt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)