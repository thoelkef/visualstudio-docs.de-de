---
title: IDebugSessionProviderEx-Schnittstelle | Microsoft Docs
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
ms.openlocfilehash: 545b60f13e86e59143ce0e57f454b13f61041f11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726930"
---
# <a name="idebugsessionproviderex-interface"></a>IDebugSessionProviderEx-Schnittstelle
Die primäre Schnittstelle bereitgestellt, die von einem Debugger IDE-Host und die Sprache initiiert Debuggen zu aktivieren. Dabei wird eine Debugsitzung für eine ausgeführte Anwendung. Diese Schnittstelle wird von der Debug-Manager implementiert.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugSessionProviderEx` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Bestimmt, ob JIT-Debuggen mit der angegebenen Anwendung möglich ist.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Startet eine Debugsitzung mit der angegebenen Anwendung an.|