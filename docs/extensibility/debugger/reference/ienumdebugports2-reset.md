---
title: IEnumDebugPorts2::Reset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugPorts2::Reset
helpviewer_keywords:
- IEnumDebugPorts2::Reset
ms.assetid: 67da406c-eadb-421e-ae12-e26e9866f262
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fdcf2fbe5349b4f404a8b1d8ad71f754a759230f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugports2reset"></a>IEnumDebugPorts2::Reset
Setzt die Enumeration auf das erste Element zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Nachdem diese Methode wird aufgerufen, den beim nächsten Aufruf der [Weiter](../../../extensibility/debugger/reference/ienumdebugports2-next.md) Methode gibt das erste Element der Enumeration.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)