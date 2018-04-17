---
title: GetVstoSolutionMetadata-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6c024d97d13c2794dd4fdaee6cfcd53d24c2e668
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata-Funktion
  Diese API unterstützt die Office-Infrastruktur und ist nicht direkt aus Ihrem Code verwendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*lpwszSolutionMetadataKey*|Verwenden Sie keine.|  
|*ppSolutionInfo*|Verwenden Sie keine.|  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Funktion erfolgreich ausgeführt wird, gibt es **S_OK**. Wenn die Funktion fehlschlägt, wird ein Fehlercode zurückgegeben.  
  
  