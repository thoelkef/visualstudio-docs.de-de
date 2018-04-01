---
title: IDebugEnumField::GetValueFromString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e98b8c8d812bfc77351b88aa85bcf9c94cd92e0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Diese Methode gibt den zugeordneten Wert durch den Namen einer Enumerationskonstante zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszValue`  
 [in] Eine Zeichenfolge, die den Namen für das Abrufen des Werts angeben. Beachten Sie, dass für C++, dies ist eine Zeichenfolge mit Breitzeichen.  
  
 `pValue`  
 [out] Gibt den zugeordneten numerischen Wert zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE`, wenn der Name nicht Teil der Enumeration oder einen Fehlercode ist.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist die Groß-/Kleinschreibung beachtet. Wenn eine Suche Groß-/Kleinschreibung (z. B. in einer anderen Sprache wie Visual Basic-Namen, in denen keine Groß-/Kleinschreibung unterschieden sind) erforderlich ist, verwenden [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)