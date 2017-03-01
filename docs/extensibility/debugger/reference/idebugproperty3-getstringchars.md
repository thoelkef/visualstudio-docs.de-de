---
title: IDebugProperty3::GetStringChars | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
caps.latest.revision: 7
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
translationtype: Machine Translation
ms.sourcegitcommit: b743df25d0d17465de411211f5b0b6893bf67f9b
ms.openlocfilehash: a9433d9914f647c43d8190fb15fb35a99bf77a7b
ms.lasthandoff: 02/22/2017

---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Ruft die Zeichenfolge, die mit dieser Eigenschaft verknüpft ist, und speichert sie in einem Benutzer bereitgestellte Puffer.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetStringChars(  
   ULONG  buflen,  
   WCHAR* rgString,  
   ULONG* pceltFetched  
);  
```  
  
```c#  
int GetStringChars(  
   uint       buflen,   
   out string rgString,   
   out uint   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `buflen`  
 [in] Maximale Anzahl von Zeichen, die der Benutzer bereitgestellte Puffer aufnehmen kann.  
  
 `rgString`  
 [out] Gibt die Zeichenfolge zurück.  
  
 [Nur C++] `rgString` ist ein Zeiger auf einen Puffer, der Unicode-Zeichen der Zeichenfolge empfängt. Dieser Puffer muss mindestens `buflen` Zeichen (nicht Bytes) groß.  
  
 `pceltFetched`  
 [out] Die Anzahl der Zeichen im Puffer gespeichert, in denen zurückgegeben wird. (Kann `NULL` in C++.)  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK`; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 In C++ muss geachtet werden, stellen Sie sicher, dass der Puffer mindestens `buflen` Unicode-Zeichen lang sein. Beachten Sie, dass ein Unicode-Zeichen 2 Bytes lang ist.  
  
> [!NOTE]
>  In C++ enthält die zurückgegebene Zeichenfolge kein abschließendes Nullzeichen. Wenn angegeben, `pceltFetched` wird die Anzahl der Zeichen in der Zeichenfolge angeben.  
  
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
