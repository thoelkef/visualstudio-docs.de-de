---
title: TASK_STATE_CANCELED-Feld | Microsoft-Dokumentation
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
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 869553b18f16135fe81d1a33e64eba1d33f0990b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515046"
---
# <a name="taskstatecanceled-field"></a>TASK_STATE_CANCELED-Feld
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [TASK_STATE_CANCELED-Feld](https://docs.microsoft.com/visualstudio/extensibility/debugger/task-state-canceled-field).  
  
Der Task wurde abgebrochen, bevor er den ausgeführten Zustand erreicht, oder er bestätigt die Abbruch und ohne Ausnahme abgeschlossen wurde.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)  
```  
  
## <a name="remarks"></a>Hinweise  
 Wenn die [M_stateFlags](../../extensibility/debugger/m-stateflags-field.md) Feld enthält diesen Wert, der <xref:System.Threading.Tasks.Task.Status%2A> -Eigenschaft gibt <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenklasse](../../extensibility/debugger/task-class-internal-members.md)

