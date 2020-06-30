---
title: Ensurevstocomponent-Funktion
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf55fc6669edd33d1b8896ee85f33ab2c04e844f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543584"
---
# <a name="ensurevstocomponent-function"></a>Ensurevstocomponent-Funktion
  Diese API unterstützt die Office-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```csharp
HRESULT EnsureVSTOComponent(
    IVSTProject *pProject
);
```

#### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pproject*|Verwenden Sie nicht.|

## <a name="return-value"></a>Rückgabewert
 Wenn die Funktion erfolgreich ausgeführt wird, wird **S_OK**zurückgegeben. Wenn die Ausführung der Funktion fehlschlägt, wird ein Fehlercode zurückgegeben.
