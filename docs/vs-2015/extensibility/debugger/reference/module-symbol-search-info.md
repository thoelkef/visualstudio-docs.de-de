---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2cfbaf8c3756bf758956d1f1e5964d8e9f8f0c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205183"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Enthält Statusinformationen zu Symbol Suchpfaden, die durchsucht wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```csharp  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwValidFields`  
 Eine Kombination von Flags aus der [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) -Enumeration, die die Art der Suchinformationen angibt, die in dieser Struktur beschrieben werden.  
  
 `bstrVerboseSearchInfo`  
 Suchpfad und Ergebnisse werden zu einer einzelnen Zeichenfolge verkettet.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur wird von einem Aufrufen der [getsymbolinfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) -Methode zurückgegeben.  
  
 Wenn das `bstrVerboseSearchInfo` Feld nicht leer ist, enthält es eine Liste der durchsuchten Pfade und die Ergebnisse dieser Suche. Die Liste wird mit einem Pfad, gefolgt von Ellipsen ("..."), gefolgt vom Ergebnis formatiert. Wenn mehr als ein Pfad Ergebnis Paar vorhanden ist, wird jedes Paar durch das Paar "\r\n" (Wagen Rücklauf/Zeilenvorschub) getrennt. Das Muster sieht wie folgt aus:  
  
 \<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>  
  
 Beachten Sie, dass der letzte Eintrag keine \r\n-Sequenz hat.  
  
 Hier ist eine mögliche `bstrVerboseSearchInfo` Zeichenfolge, die an Standard out gesendet wurde.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
