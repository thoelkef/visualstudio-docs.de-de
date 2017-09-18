---
title: "MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_SYMBOL_SEARCH_INFO"
helpviewer_keywords: 
  - "MODULE_SYMBOL_SEARCH_INFO-Struktur"
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Enthält Statusinformationen zu Symbolsuchpfaden, die durchsucht wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```c#  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwValidFields`  
 Eine Kombination aus Flags aus der [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) -Enumeration, die die Art der Suchinformationen, die in dieser Struktur beschrieben angibt.  
  
 `bstrVerboseSearchInfo`  
 Suchpfad und Ergebnisse in einer einzelnen Zeichenfolge verkettet.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zurückgegeben, von einem Aufruf der [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) Methode.  
  
 Wenn die `bstrVerboseSearchInfo` Feld nicht leer, wird er enthält eine Liste von Pfaden, die durchsucht und die Ergebnisse dieses Vergleichs. Die Liste wird mit einem Pfad, gefolgt von Ellipsen ("..."), gefolgt von dem Ergebnis formatiert. Wenn Sie mehrere Path-Ergebnis-Paar vorhanden ist, wird jedes Paar durch ein "\r\n" (Return – Wagenrücklauf/Zeilenvorschub) getrennt. Das Muster sieht folgendermaßen aus:  
  
 \< Pfad>... \< Ergebnis>\r\n \< Pfad>... \< Ergebnis>\r\n \< Pfad>... \< Ergebnis>  
  
 Beachten Sie, dass der letzte Eintrag nicht nacheinander \r\n.  
  
 Hier ist ein mögliches `bstrVerboseSearchInfo` Zeichenfolge, die an die Standardausgabe gesendet wurde.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)