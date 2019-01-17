---
title: IDebugSessionProviderEx-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fae1cf673f47d3be586f83320b2d2c38c817e2cf
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349217"
---
# <a name="idebugsessionproviderex-interface"></a>IDebugSessionProviderEx-Schnittstelle
Die primäre Schnittstelle bereitgestellt, die von einem Debugger-IDE, um den Host und Sprache – initiierten Debuggen zu aktivieren. Er richtet eine Debugsitzung für eine ausgeführte Anwendung. Diese Schnittstelle wird von der Debug-Manager implementiert.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugSessionProviderEx` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Bestimmt, ob Just-in-Time-Debuggen mit der angegebenen Anwendung möglich ist.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Startet eine Debugsitzung mit der angegebenen Anwendung.|