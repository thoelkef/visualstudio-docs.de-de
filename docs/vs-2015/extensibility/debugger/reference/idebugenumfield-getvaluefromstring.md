---
title: 'Idebugenenfield:: getvaluefromstring | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f553b7f019dd89af771e057a46a11b1affed1308
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188942"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode gibt den Wert zurück, der dem Namen einer Enumerationskonstante zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Eine Zeichenfolge, die den Namen angibt, für den der Wert zu erhalten ist. Beachten Sie, dass dies für C++ eine Zeichenfolge mit breit Zeichen ist.  
  
 `pValue`  
 vorgenommen Gibt den zugeordneten numerischen Wert zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben `S_FALSE` , wenn der Name nicht Teil der-Enumeration ist, oder ein Fehlercode.  
  
## <a name="remarks"></a>Bemerkungen  
 Bei dieser Methode wird die Groß-/Kleinschreibung beachtet. Wenn eine Suche ohne Berücksichtigung der Groß-/Kleinschreibung erforderlich ist (z. b. in einer Sprache wie Visual Basic, in der die Groß-/Kleinschreibung nicht beachtet wird), verwenden Sie [getvaluefromstringcaseinsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugenenfield](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
