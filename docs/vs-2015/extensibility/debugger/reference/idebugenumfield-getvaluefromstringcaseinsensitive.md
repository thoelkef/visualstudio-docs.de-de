---
title: 'Idebugenenfield:: getvaluefromstringcaseinsensitive | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: efe94a721c432cb1284df299ca267271ab5bef4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188933"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode verwendet die Suche ohne Beachtung der Groß-/Kleinschreibung, um den Wert zurückzugeben, der dem Namen einer Enumerationskonstante zugeordnet ist  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromStringCaseInsensitive(  
   string    pszValue,   
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszValue`  
 in Eine Zeichenfolge, die den Namen angibt, für den der Wert zu erhalten ist. Beachten Sie, dass dies für C++ eine Zeichenfolge mit breit Zeichen ist.  
  
 `pValue`  
 vorgenommen Gibt den zugeordneten numerischen Wert zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben `S_FALSE` , wenn der Name nicht Teil der-Enumeration ist, oder ein Fehlercode.  
  
## <a name="remarks"></a>Bemerkungen  
 Bei dieser Methode wird Groß-/Kleinschreibung nicht beachtet. Wenn eine Suche nach Groß-/Kleinschreibung erforderlich ist (z. b. in einer Sprache wie C++, bei der bei Namen die Groß-/Kleinschreibung beachtet wird), verwenden Sie [getvaluefromstring](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugenenfield](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
