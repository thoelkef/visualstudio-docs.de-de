---
title: IMachineDebugManagerEvents-Schnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: f9aab3d7abeecd22e830c68f174896df0e7df2da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344027"
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents-Schnittstelle
Signaländerungen in der ausgeführten Anwendungsliste, die vom computerbasierten Debug-Manager verwaltet werden. Diese Schnittstelle kann durch den Debugger-IDE verwendet werden, um eine dynamische Liste der Anwendungen anzuzeigen.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IMachineDebugManagerEvents` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Behandelt das Ereignis, wenn die Ausführung eine Anwendung hinzugefügt wird Liste der Anwendungen.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Behandelt das Ereignis, wenn eine Anwendung, aus der ausgeführten entfernt wird Anwendungsliste.|