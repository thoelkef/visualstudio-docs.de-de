---
title: "IDebugModule3::GetSymbolInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3::GetSymbolInfo"
helpviewer_keywords: 
  - "Methode "getsymbolinfo""
  - "IDebugModule3::GetSymbolInfo-Methode"
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IDebugModule3::GetSymbolInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Liste der Pfade, die für Symbole als auch die Ergebnisse der Suche nach jeder Pfad durchsucht werden.  
  
## Syntax  
  
```cpp#  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```c#  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### Parameter  
 `dwFields`  
 \[in\] Eine Kombination von Flags aus der [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) Enumeration, angibt, welche Felder der `pInfo` ausgefüllt werden.  
  
 `pInfo`  
 \[out\] Ein [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) \-Struktur, deren Mitglieder sind, die mit den angegebenen Informationen gefüllt werden. Wenn dies ein null\-Wert ist, gibt diese Methode `E_INVALIDARG`.  
  
## Rückgabewert  
 Wenn die Methode erfolgreich ist, gibt es `S_OK`andernfalls wird einen Fehlercode zurückgegeben.  
  
> [!NOTE]
>  Die zurückgegebene Zeichenfolge \(in der `MODULE_SYMBOL_SEARCH_INFO` Struktur\) leer sein, wenn `S_OK` zurückgegeben wird. In diesem Fall ist keine Suche Informationen zurückgeben.  
  
## Hinweise  
 Wenn die `bstrVerboseSearchInfo` Feld der `MODULE_SYMBOL_SEARCH_INFO` Struktur ist nicht leer, und sie enthält eine Liste der Pfade durchsucht und die Ergebnisse dieser Suche. Die Liste wird mit einem Pfad, gefolgt von Ellipsen \("..."\), gefolgt von dem Ergebnis formatiert. Wenn Sie mehrere Path\-Ergebnis\-Paar vorhanden ist, wird jedes Paar durch ein "\\r\\n" \(Return – Wagenrücklauf\/Zeilenvorschub\) getrennt. Das Muster sieht folgendermaßen aus:  
  
 \< Pfad \>... \< Ergebnis \> \\r\\n \< Pfad \>... \< Ergebnis \> \\r\\n \< Pfad \>... \< Ergebnis \>  
  
 Beachten Sie, dass der letzte Eintrag nicht nacheinander \\r\\n.  
  
## Beispiel  
 In diesem Beispiel gibt diese Methode die Pfade mit drei unterschiedliche Ergebnisse zurück. Jede Zeile wird mit ein paar Wagenrücklauf\-\/ Zeilenvorschub beendet. Die Ausgabe gibt die Ergebnisse der Suche als einzelne Zeichenfolge.  
  
> [!NOTE]
>  Ein Status\-Ergebnis ist alles, was die "..." bis zum Ende der Zeile unmittelbar folgt.  
  
```cpp#  
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)  
{  
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };  
    HRESULT hr;  
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);  
    if (SUCCEEDED(hr)) {  
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;  
        if (searchInfo.Length() != 0) {  
            std::wcout << (wchar_t *)(BSTR)searchInfo;  
            std::wcout << std::endl;  
        }  
    }  
}  
```  
  
 **c:\\symbols\\user32.pdb... Die Datei wurde nicht gefunden. c:\\winnt\\symbols\\user32.pdb... Version stimmt nicht überein. \\\\symbols\\symbols\\user32.dll\\0a8sd0ad8ad\\user32.pdb... Symbole geladen.**   
## Siehe auch  
 [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)