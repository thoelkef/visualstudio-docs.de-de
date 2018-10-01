---
title: IDebugCodeContext3 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7064cddbf81a01e7d55d64249d4ff4da6e585728
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520810"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugCodeContext3](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcodecontext3).  
  
Erweitert die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Schnittstelle für den Abruf von Modul und die Prozess-Schnittstellen zu aktivieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Von der Debug-Engines implementiert und von der [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] -Paket debuggen.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den Methoden für die `IDebugCodeContext2` Schnittstelle, die diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Ruft einen Verweis auf die Schnittstelle von der Debug-Modul ab.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Ruft einen Verweis auf die Schnittstelle von der Debug-Prozess ab.|  
  
## <a name="remarks"></a>Hinweise  
 Dies ist eine optionale Schnittstelle, die in der Regel nicht unbedingt implementiert werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

