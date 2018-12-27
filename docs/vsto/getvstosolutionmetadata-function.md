---
title: GetVstoSolutionMetadata-Funktion
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: baa5cf48d317da80f78d19a1b72f81824b1bed62
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647265"
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata-Funktion
  Diese API unterstützt die Office-Infrastruktur und ist nicht direkt aus Ihrem Code verwendet werden soll.  
  
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
|*ppSolutionInfo*|Verwenden Sie nicht.|  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Funktion erfolgreich ist, gibt es **S_OK**. Wenn die Funktion fehlschlägt, wird einen Fehlercode zurückgegeben.  
  
  