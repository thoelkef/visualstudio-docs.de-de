---
title: EnsureVSTOComponent-Funktion
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
ms.openlocfilehash: 39dcdcc5e3b8e6e5bc5834e7e05ea22516d8c7e6
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648612"
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
  
  