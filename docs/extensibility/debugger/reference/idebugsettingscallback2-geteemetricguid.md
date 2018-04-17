---
title: IDebugSettingsCallback2::GetEEMetricGuid | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricGuid
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 040cae9a9c5bdba36c984f4aeef33beae42a0355
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsettingscallback2geteemetricguid"></a>IDebugSettingsCallback2::GetEEMetricGuid
Ruft den eindeutigen Bezeichner für eine Expression Evaluator Metrik angegebenen Namen ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetEEMetricGuid(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   GUID*   pguidValue  
);  
```  
  
```csharp  
HRESULT GetEEMetricGuid(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out Guid pguidValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `guidLang`  
 [in] Eindeutiger Bezeichner der Programmiersprache.  
  
 `guidVendor`  
 [in] Eindeutiger Bezeichner des Herstellers.  
  
 `pszMetric`  
 [in] Der Name der Metrik.  
  
 `pguidValue`  
 [out] Gibt den eindeutigen Bezeichner der Metrik an.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)