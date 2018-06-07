---
title: IWefDebuggingSupport-Schnittstelle
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 351fb69b99393a10518168f4f9b01efe1f9efaa7
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572672"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport-Schnittstelle
  Implementiert eine debugging-Umgebung, z. B. Visual Studio zum Debuggen von apps für Office zu erleichtern. Die Office-Anwendung, z. B. Word oder Excel, erhält diese Schnittstelle über Visual Studio und ruft dann die Methoden für die Schnittstelle an bestimmten Punkten während der Debugsitzung.  
  
## <a name="syntax"></a>Syntax  
  
```csharp 
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle enthält die Methoden, die die IWefDebuggingSupport-Schnittstelle definiert.  
  
|name|Beschreibung|  
|----------|-----------------|  
|[GetAutoInsertExtensions-Methode](../vsto/getautoinsertextensions-method.md)|Ruft Informationen zu den apps für Office, die während des Debuggens automatisch eingefügt werden sollen.|  
|[SetWefProcessId-Methode](../vsto/setwefprocessid-method.md)|Enthält die Prozess-ID, die Inhalt Web Erweiterungen Framework (WEF) ausgeführt wird.|  
  
  