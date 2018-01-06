---
title: IDebugModule3::GetSymbolInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8648e591e545db73b636c6b21fcbcaa1d1afb640
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Ruft eine Liste von Pfaden, die für Symbole als auch die Ergebnisse der Suche jeder Pfad durchsucht werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```csharp  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFields`  
 [in] Eine Kombination aus Flags aus der [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) Enumeration, angibt, welche Felder der `pInfo` ausgefüllt werden.  
  
 `pInfo`  
 [out] Ein [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) -Struktur, deren Mitglieder, die mit den angegebenen Informationen ausgefüllt sind. Wenn dies ein null-Wert ist, gibt diese Methode `E_INVALIDARG`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Methode erfolgreich ist, gibt es `S_OK`ist, andernfalls einen Fehlercode zurückgegeben.  
  
> [!NOTE]
>  Die zurückgegebene Zeichenfolge (in der `MODULE_SYMBOL_SEARCH_INFO` Struktur) möglicherweise leere selbst wenn `S_OK` zurückgegeben wird. In diesem Fall ist keine Suche Informationen zurückgeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die `bstrVerboseSearchInfo` Feld der `MODULE_SYMBOL_SEARCH_INFO` Struktur ist nicht leer und enthält eine Liste von Pfaden, die durchsucht und die Ergebnisse dieses Vergleichs. Die Liste wird mit einem Pfad, gefolgt von einem Auslassungszeichen ("..."), gefolgt von dem Ergebnis formatiert. Wenn mehr als ein Paar von Path-Ergebnis vorhanden ist, wird jedes Paar durch ein Paar aus "\r\n" (Return – Wagenrücklauf/Zeilenvorschub) getrennt. Das Muster sieht wie folgt:  
  
 \<Pfad >... \<Ergebnis > \r\n\<Pfad >... \<Ergebnis > \r\n\<Pfad >... \<Ergebnis >  
  
 Beachten Sie, dass der letzte Eintrag nicht mit eine Sequenz \r\n verfügt.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel gibt diese Methode drei Pfade mit drei unterschiedliche Ergebnisse zurück. Jede Zeile wird mit ein paar Zeilenschaltung-/ Zeilenvorschub beendet. Die Beispielausgabe druckt nur die Suchergebnisse als eine einzelne Zeichenfolge.  
  
> [!NOTE]
>  Ein Status-Ergebnis ist alles, was unmittelbar nach dem "..." bis zum Ende der Zeile.  
  
```cpp  
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
  
 **c:\symbols\user32.pdb... Die Datei wurde nicht gefunden.**  
**c:\winnt\symbols\user32.pdb... Version stimmt nicht überein.**  
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbole, die geladen werden.**   
## <a name="see-also"></a>Siehe auch  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)