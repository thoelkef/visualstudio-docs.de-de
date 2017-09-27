---
title: IDebugSettingsCallback2::GetEEMetricString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricString
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 60fe2d13216964c2132901f92f762824bcba9ef3
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="idebugsettingscallback2geteemetricstring"></a>IDebugSettingsCallback2::GetEEMetricString
Ruft den Wert ein Expression Evaluator Metrik angegebenen Namen ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetEEMetricString(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   BSTR*   pbstrValue  
);  
```  
  
```csharp  
private int GetEEMetricString(  
   ref Guid   guidLang,  
   ref Guid   guidVendor,  
   string     pszMetric,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `guidLang`  
 [in] Eindeutiger Bezeichner der Programmiersprache.  
  
 `guidVendor`  
 [in] Eindeutiger Bezeichner des Herstellers.  
  
 `pszMetric`  
 [in] Der Name der Metrik.  
  
 `pbstrValue`  
 [out] Die Zeichenfolge metrischer Wert zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
