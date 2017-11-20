---
title: IWefDebuggingSupport-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7768465f46e5344b88da9006a7de2396e3b75ba6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport-Schnittstelle
  Implementiert eine debugging-Umgebung, z. B. Visual Studio zum Debuggen von apps für Office zu erleichtern. Die Office-Anwendung, z. B. Word oder Excel, erhält diese Schnittstelle über Visual Studio und ruft dann die Methoden für die Schnittstelle an bestimmten Punkten während der Debugsitzung.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
  
|Name|Beschreibung|  
|----------|-----------------|  
|[GetAutoInsertExtensions-Methode](../vsto/getautoinsertextensions-method.md)|Ruft Informationen zu den apps für Office, die während des Debuggens automatisch eingefügt werden sollen.|  
|[SetWefProcessId-Methode](../vsto/setwefprocessid-method.md)|Enthält die Prozess-ID, die Inhalt Web Erweiterungen Framework (WEF) ausgeführt wird.|  
  
  