---
title: IDebugSettingsCallback2::GetEEMetricFile | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricFile
ms.assetid: 3a0bf9e5-bbd2-4d15-840d-8244732787fc
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b48cdbe96f48f3c685dee20fd06353ecc39d3b21
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912343"
---
# <a name="idebugsettingscallback2geteemetricfile"></a>IDebugSettingsCallback2::GetEEMetricFile
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Expression Evaluator Metrik Datei erhält den Namen oder die Metrik ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetEEMetricFile(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   BSTR*   pbstrValue  
);  
```  
  
```csharp  
private int GetEEMetricFile(  
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
 [out] Gibt den Inhalt der Datei Metrik als Zeichenfolge zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

