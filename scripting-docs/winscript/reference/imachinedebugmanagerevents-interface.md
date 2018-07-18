---
title: IMachineDebugManagerEvents-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 369dc8d182efe7bf9697454d0e4b1c9c1a10c027
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727630"
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents-Schnittstelle
Änderungen bei der Ausführung signalisiert Anwendungsliste, die von der Computer-Manager verwaltet wird. Diese Schnittstelle kann vom Debugger IDE verwendet werden, um eine dynamische Liste von Anwendungen anzuzeigen.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IMachineDebugManagerEvents` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Behandelt das Ereignis, wenn die Ausführung eine Anwendung hinzugefügt wird-Anwendungsliste.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Behandelt das Ereignis, wenn die Ausführung eine Anwendung entfernt wird Anwendungsliste.|