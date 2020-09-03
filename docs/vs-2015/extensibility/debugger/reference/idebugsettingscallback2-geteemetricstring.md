---
title: 'IDebugSettingsCallback2:: geteemetricstring | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricString
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f498bb22c5830434d11a560fa139e77850244b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155177"
---
# <a name="idebugsettingscallback2geteemetricstring"></a>IDebugSettingsCallback2::GetEEMetricString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Wert Zeichenfolge einer Ausdrucks Auswertungs Metrik unter Berücksichtigung des Namens ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Eindeutiger Bezeichner der Programmiersprache.  
  
 `guidVendor`  
 in Eindeutiger Bezeichner des Anbieters.  
  
 `pszMetric`  
 in Der Name der Metrik.  
  
 `pbstrValue`  
 vorgenommen Gibt die metrikwertzeichenfolge zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
