---
title: IRemoteDebugApplication110-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110 Interface
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d384cea22b79b2a7ca9af3424d053fb3062d79a3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729540"
---
# <a name="iremotedebugapplication110-interface"></a>IRemoteDebugApplication110-Schnittstelle
Wird verwendet, um neue Funktionen bereitzustellen, die vom Skriptdebugger aufgerufen werden kann und in-Process-Aufrufer.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IRemoteDebugApplication110`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|Wird aufgerufen, um Optionen für den Debugger zu aktualisieren. Die Optionen standardmäßig auf 0 (SDO_NONE).|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|Gibt den aktuellen Satz von Optionen, die aktiviert sind.|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|Gibt den Hauptthread für Hosts, die SetSite aufrufen.|