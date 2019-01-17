---
title: IApplicationDebuggerUI-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e3c5f9e4cabeb4fba31bb039a7cf673ca1759860
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348905"
---
# <a name="iapplicationdebuggerui-interface"></a>IApplicationDebuggerUI-Schnittstelle
Durch die integrierte Entwicklungsumgebung (IDE) von Debugger implementiert (zusätzlich zu `IApplicationDebugger`) zu einer externen Komponente mehr Kontrolle über die Benutzeroberfläche (UI) des Debuggers haben.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IApplicationDebuggerUI` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Bringt das Fenster mit dem angegebenen Debug-Dokument oben im Debugger-Benutzeroberfläche.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Bringt das Fenster, die den angegebenen Dokument-Kontext oben in der Debugger-Benutzeroberfläche und führt einen Bildlauf durch das Fenster, um den Kontext.|