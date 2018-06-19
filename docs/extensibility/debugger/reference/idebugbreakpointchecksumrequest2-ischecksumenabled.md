---
title: IDebugBreakpointChecksumRequest2::IsChecksumEnabled | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2::IsChecksumEnabled
ms.assetid: 8b1853b5-745c-4cd6-88a9-ce0673971bb0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 34afc9af142371537c82effbfb8c636bcba09dbd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098978"
---
# <a name="idebugbreakpointchecksumrequest2ischecksumenabled"></a>IDebugBreakpointChecksumRequest2::IsChecksumEnabled
Bestimmt, ob die Prüfsumme für dieses Dokument aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsChecksumEnabled(   
   BOOL *pfChecksumEnabled  
);  
```  
  
```csharp  
public int IsChecksumEnabled(   
   out int pfChecksumEnabled  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pfChecksumEnabled`  
 [out] Gibt TRUE zurück, wenn die Prüfsumme aktiviert ist. Andernfalls wird "false" zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)