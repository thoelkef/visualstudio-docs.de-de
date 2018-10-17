---
title: IDebugProgram2::WriteDump | Microsoft-Dokumentation
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
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 42506dc9e4d9fdd0d85f697c4ea667705fa2b6be
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190098"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Schreibt einen Dump in eine Datei an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

