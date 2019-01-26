---
title: IDebugProperty3::GetStringChars | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c70a2f9dd7e5ef52a0360ac59d995ddbd933c40
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991202"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Ruft die Zeichenfolge, die dieser Eigenschaft zugeordnet, und speichert ihn in einem vom Benutzer bereitgestellten Puffer.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetStringChars(  
   ULONG  buflen,  
   WCHAR* rgString,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetStringChars(  
   uint       buflen,   
   out string rgString,   
   out uint   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `buflen`  
 [in] Maximale Anzahl von Zeichen kann es sich um der Benutzer bereitgestellten Puffer enthalten.  
  
 `rgString`  
 [out] Gibt die Zeichenfolge zurück.  
  
 [Nur für C++], `rgString` ist ein Zeiger auf einen Puffer, die Unicode-Zeichen der Zeichenfolge empfängt. Dieser Puffer muss mindestens `buflen` (nicht Bytes) Zeichen lang sein.  
  
 `pceltFetched`  
 [out] Die Anzahl der Zeichen, die tatsächlich im Puffer gespeichert, in dem zurückgegeben wird. (Kann `NULL` in C++.)  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück.  
  
## <a name="remarks"></a>Hinweise  
 In C++ müssen geachtet werden, stellen Sie sicher, dass der Puffer mindestens `buflen` Unicode-Zeichen lang sein. Beachten Sie, dass ein Unicode-Zeichen mit 2 Bytes lang ist.  
  
> [!NOTE]
>  In C++ enthält die zurückgegebene Zeichenfolge kein abschließendes Nullzeichen. Wenn angegeben, `pceltFetched` geben die Anzahl der Zeichen in der Zeichenfolge.  
  
## <a name="example"></a>Beispiel  
 
```cpp  
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)  
{  
    CStringW returnString = L"";  
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;  
    If (pProp3 != NULL) {  
        ULONG dwStrLen = 0;  
        HRESULT hr;  
        hr = pProp3->GetStringCharLength(&dwStrLen);  
        if (SUCCEEDED(hr) && dwStrLen > 0) {  
            ULONG dwRead;  
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);  
            hr = pProp3->GetStringChars(dwStrLen,  
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),  
                                        &dwRead);  
        }  
    }  
    return(returnString);
}
```    
  
## <a name="see-also"></a>Siehe auch  
 [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)