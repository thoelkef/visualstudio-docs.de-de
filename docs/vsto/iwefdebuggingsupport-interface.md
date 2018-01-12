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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7b132c51e12d553bcd6e722e87c8aeee96be5e5c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
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
  
|name|Beschreibung|  
|----------|-----------------|  
|[GetAutoInsertExtensions-Methode](../vsto/getautoinsertextensions-method.md)|Ruft Informationen zu den apps für Office, die während des Debuggens automatisch eingefügt werden sollen.|  
|[SetWefProcessId-Methode](../vsto/setwefprocessid-method.md)|Enthält die Prozess-ID, die Inhalt Web Erweiterungen Framework (WEF) ausgeführt wird.|  
  
  