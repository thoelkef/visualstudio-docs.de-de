---
title: "IActiveScriptStringCompare::StrComp | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStringCompare.StrComp
apilocation: scrobj.dll
helpviewer_keywords: 
  - "StrComp-Methode, IActiveScriptStringCompare-Schnittstelle"
ms.assetid: 124d1281-8037-4766-a2a1-61244ac1f114
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStringCompare::StrComp
Definiert die Zeichenfolgenvergleichsmethode für das Skriptmodul.  
  
## Syntax  
  
```  
HRESULT StrComp(  
// The first string:  
    [in] BSTR bszStr1,    
// The second string:   
    [in] BSTR bszStr2,    
// The result of the comparison:  
    [out, retval] LONG* iRet   
);  
```  
  
#### Parameter  
 `bszStr1`  
 Die erste Zeichenfolge.  
  
 `bszStr2`  
 Die zweite Zeichenfolge.  
  
 `iRet`  
 Das Ergebnis des Vergleichs.  0, wenn  `bszStr1` und `bszStr2` identisch sind; \-1, wenn `bszStr1` \< `bszStr2`; 1, wenn `bszStr1` \> `bszStr2`.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument ist ungültig.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, ist das Skriptmodul noch nicht geladen wurde oder initialisiert wurden\).|  
  
## Hinweise  
 Diese Methode wird jedes Mal aufgerufen, dass ein Zeichenfolgenvergleich ausgeführt wird.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie die Zeichenfolgenvergleichsfunktion überladen werden.  Überladen ist zulässig, wenn Sie [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) verwenden, um SCRIPTPROP\_STRINGCOMPAREINSTANCE festzulegen.  
  
```cpp#  
cpp_quote("// {58562769-ED52-42f7-8403-4963514E1F11}")  
cpp_quote("DEFINE_GUID(IID_IActiveScriptStringCompare, 0x58562769,   
    0xED52, 0x42f7, 0x84, 0x03, 0x49, 0x63, 0x51, 0x4E, 0x1F, 0x11);")  
cpp_quote("")  
  
cpp_quote("#define SCRIPTPROP_INTEGERMODE              0x00003000")  
cpp_quote("#define SCRIPTPROP_STRINGCOMPAREINSTANCE    0x00003001")  
cpp_quote("")  
interface IActiveScriptStringCompare;  
[  
         object,  
         uuid(58562769-ED52-42f7-8403-4963514E1F11),  
         pointer_default(unique)  
]  
interface IActiveScriptStringCompare : IUnknown  
{  
        // StrComp  
        //     bszStr1: first string  
        //     bszStr2: second string  
        //     iRet: 0 if identical, -1 if bszStr1 < bszStr2, 1 if   
        //         bszStr1 > bszStr2  
        //            
        //     Return values:  
        //         S_OK: Success  
        //         E_NOTIMPL: Not implemented  
        //  
        HRESULT StrComp(  
                [in] BSTR bszStr1,  
                [in] BSTR bszStr2,  
                [out, retval] LONG* iRet  
        );  
}  
```  
  
## Siehe auch  
 [IActiveScriptStringCompare\-Schnittstelle](../../winscript/reference/iactivescriptstringcompare-interface.md)