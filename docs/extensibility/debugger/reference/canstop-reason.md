---
title: CANSTOP_REASON | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CANSTOP_REASON
helpviewer_keywords: CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 98b1e4a9db18490079dd443cb296481aed64376a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="canstopreason"></a>CANSTOP_REASON
Verwendet, um zu bestimmen, ob ein Programm nach Erreichen von einem bestimmten Zeitpunkt während der Ausführung beenden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>Member  
 CANSTOP_ENTRYPOINT  
 Gibt den Einstiegspunkt des angegebenen Programms an.  
  
 CANSTOP_STEPIN  
 Gibt an, in eine Funktion schrittweise durchlaufen.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) Methode, um mit der Sitzung Debug-Manager (SDM) zu ermitteln, ob es angemessen, nach dem Erreichen des Einstiegspunkt des Programms oder nach einem Einzelschritt in eine Funktion oder Methode beendet ist.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)