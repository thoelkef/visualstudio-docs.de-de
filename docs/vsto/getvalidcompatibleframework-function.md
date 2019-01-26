---
title: GetValidCompatibleFramework-Funktion
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
ms.openlocfilehash: 79b97867a3a5c87f1e208d93efacea711ba71efc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869306"
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
