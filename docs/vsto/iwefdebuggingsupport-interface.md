---
title: Iwef debuggingsupport-Schnittstelle
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0a4883d36c1833c66a2539380184521b070f5c2a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544728"
---
# <a name="iwefdebuggingsupport-interface"></a>Iwef debuggingsupport-Schnittstelle
  Wird von einer Debugumgebung implementiert, z. b. Visual Studio, um das Debuggen von Apps für Office zu vereinfachen. Die Office-Anwendung, z. b. Word oder Excel, ruft diese Schnittstelle von Visual Studio ab und ruft dann an bestimmten Punkten während der Debugsitzung Methoden für die Schnittstelle auf.

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
 In der folgenden Tabelle werden die Methoden aufgelistet, die von der iwefdebuggingsupport-Schnittstelle definiert werden.

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Getautoinsertextensions-Methode](../vsto/getautoinsertextensions-method.md)|Ruft Informationen zu den Apps für Office ab, die während des Debuggens automatisch eingefügt werden sollen.|
|[Setwef ProcessID-Methode](../vsto/setwefprocessid-method.md)|Stellt den Prozess Bezeichner bereit, mit dem WEF-Inhalte (Web Extensions Framework) ausgeführt werden.|
