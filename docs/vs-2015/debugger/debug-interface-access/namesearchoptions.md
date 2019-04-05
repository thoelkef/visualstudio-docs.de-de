---
title: NameSearchOptions | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 29b6500ab138883c8cbf71eda5a0afad1329494e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946711"
---
# <a name="namesearchoptions"></a>NameSearchOptions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt die Suchoptionen für Symbol und den Dateinamen an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## <a name="elements"></a>Elements  
 `nsNone`  
 Es wurden keine Optionen angegeben.  
  
 `nsfCaseSensitive`  
 Wendet eine namensübereinstimmung der Groß-/Kleinschreibung an.  
  
 `nsfCaseInsensitive`  
 Wendet eine namensübereinstimmung der Groß-/Kleinschreibung an.  
  
 `nsfFNameExt`  
 Namen behandelt, als Pfade und eine namensübereinstimmung filename.ext gilt.  
  
 `nsfRegularExpression`  
 Wendet die Groß-/Kleinschreibung namensübereinstimmung mithilfe von Sternchen (*) und Fragezeichen (?) als Platzhalter.  
  
 `nsfUndecoratedName`  
 Gilt nur für Symbole, die nicht ergänzten Form und ergänzte Namen haben.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte aus dieser Enumeration werden für die folgenden Methoden übergeben:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Anforderungen  
 Header: dia2.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
