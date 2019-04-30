---
title: IWefDebuggingSupport-Schnittstelle
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a71adf5371275fbbdc19cdf09be96ef900ec073d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583762"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport-Schnittstelle
  Implementiert, indem eine debugging-Umgebung wie Visual Studio zum Debuggen von apps für Office zu erleichtern. Die Office-Anwendung wie Word oder Excel, ruft diese Schnittstelle in Visual Studio, und ruft dann die Methoden der Schnittstelle an bestimmten Punkten während der Debugsitzung.

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

|Name|Beschreibung|
|----------|-----------------|
|[GetAutoInsertExtensions-Methode](../vsto/getautoinsertextensions-method.md)|Ruft Informationen zu den apps für Office, die während des Debuggens automatisch eingefügt werden sollen.|
|[SetWefProcessId-Methode](../vsto/setwefprocessid-method.md)|Enthält die Prozess-ID, die Inhalte der Web-Extensions-Framework (WEF) ausgeführt wird.|
