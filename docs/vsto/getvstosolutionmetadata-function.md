---
title: Getvstosolutionmetadata-Funktion
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
ms.openlocfilehash: aebbedaab7e7ac342f6d6ace191d820f6a0c8090
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520184"
---
# <a name="getvstosolutionmetadata-function"></a>Getvstosolutionmetadata-Funktion
  Diese API unterstützt die Office-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```csharp
HRESULT WINAPI GetVstoSolutionMetadata(
    LPCWSTR lpwszSolutionMetadataKey,
    ISolutionMetadata** ppSolutionInfo
);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*lpwszSolutionMetadataKey*|Verwenden Sie nicht.|
|*ppsolutioninfo*|Verwenden Sie nicht.|

## <a name="return-value"></a>Rückgabewert
 Wenn die Funktion erfolgreich ausgeführt wird, wird **S_OK**zurückgegeben. Wenn die Ausführung der Funktion fehlschlägt, wird ein Fehlercode zurückgegeben.
