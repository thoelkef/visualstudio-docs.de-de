---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c4afe972f4f5218c04c1bd8a9223c7b317dc3ab3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO
Enthält Statusinformationen zu Symbolsuchpfaden, die durchsucht wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 Eine Kombination aus Flags aus der [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) -Enumeration, die die Art der Suchinformationen, die in dieser Struktur beschrieben angibt.  
  
 `bstrVerboseSearchInfo`  
 Suchpfad und Ergebnisse in einer einzelnen Zeichenfolge verkettet.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zurückgegeben, von einem Aufruf der [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) Methode.  
  
 Wenn die `bstrVerboseSearchInfo` Feld nicht leer, wird er enthält eine Liste von Pfaden, die durchsucht und die Ergebnisse dieses Vergleichs. Die Liste wird mit einem Pfad, gefolgt von einem Auslassungszeichen ("..."), gefolgt von dem Ergebnis formatiert. Wenn mehr als ein Paar von Path-Ergebnis vorhanden ist, wird jedes Paar durch ein Paar aus "\r\n" (Return – Wagenrücklauf/Zeilenvorschub) getrennt. Das Muster sieht wie folgt:  
  
 \<Pfad >... \<Ergebnis > \r\n\<Pfad >... \<Ergebnis > \r\n\<Pfad >... \<Ergebnis >  
  
 Beachten Sie, dass der letzte Eintrag nicht mit eine Sequenz \r\n verfügt.  
  
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