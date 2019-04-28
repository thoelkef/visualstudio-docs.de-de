---
title: EnsureVSTOComponent-Funktion
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
ms.openlocfilehash: f99ccb4cb76f942852716abf1fcb0c0f280decbd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797610"
---
# <a name="ensurevstocomponent-function"></a>EnsureVSTOComponent-Funktion
  Diese API unterstützt die Office-Infrastruktur und ist nicht direkt aus Ihrem Code verwendet werden soll.

## <a name="syntax"></a>Syntax

```csharp
HRESULT EnsureVSTOComponent(
    IVSTProject *pProject
);
```

#### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*pProject*|Verwenden Sie nicht.|

## <a name="return-value"></a>Rückgabewert
 Wenn die Funktion erfolgreich ist, gibt es **S_OK**. Wenn die Funktion fehlschlägt, wird einen Fehlercode zurückgegeben.
