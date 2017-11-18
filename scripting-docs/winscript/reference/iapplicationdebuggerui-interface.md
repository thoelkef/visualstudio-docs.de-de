---
title: IApplicationDebuggerUI-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbaa04f6790ffc4d80447a6745ca82cc8dba6802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerui-interface"></a>IApplicationDebuggerUI-Schnittstelle
Von der integrierten Entwicklungsumgebung (IDE) von Debugger implementiert (zusätzlich zum `IApplicationDebugger`) auf einer externen Komponente mehr Kontrolle über die Benutzeroberfläche (UI) des Debuggers erhalten.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IApplicationDebuggerUI` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Schaltet das Fenster mit dem die angegebene Debug-Dokument in der Debugger nach oben Benutzeroberfläche.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Schaltet das Fenster mit den angegebenen Dokumentenkontext in der Debugger-Benutzeroberfläche nach oben, und verschiebt das Fenster, um den Kontext.|