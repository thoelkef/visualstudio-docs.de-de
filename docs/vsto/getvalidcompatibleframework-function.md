---
title: GetValidCompatibleFramework-Funktion
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
ms.openlocfilehash: b93e0de5f1d8c1d4e93189e7bfee36d44db19319
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648877"
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework-Funktion
  Diese API unterstützt die Office-Infrastruktur und ist nicht direkt aus Ihrem Code verwendet werden soll.  

## <a name="syntax"></a>Syntax  

```csharp 
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  

### <a name="parameters"></a>Parameter  

|Parameter|Beschreibung|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|Verwenden Sie nicht.|  
|*pbstrValidFrameworkTag*|Verwenden Sie nicht.|  

## <a name="return-value"></a>Rückgabewert  
 Wenn die Funktion erfolgreich ist, gibt es **S_OK**. Wenn die Funktion fehlschlägt, wird einen Fehlercode zurückgegeben.  

