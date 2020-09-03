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
ms.openlocfilehash: 6d721ebc5849fc459d24173ad0500b4b1c12260f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182980"
---
# <a name="namesearchoptions"></a>NameSearchOptions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt die Suchoptionen für Symbol-und Dateinamen an.  
  
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
  
## <a name="elements"></a>Elemente  
 `nsNone`  
 Es wurden keine Optionen angegeben.  
  
 `nsfCaseSensitive`  
 Wendet eine namens Übereinstimmung nach Groß-/Kleinschreibung  
  
 `nsfCaseInsensitive`  
 Wendet die Groß-/Kleinschreibung nicht an.  
  
 `nsfFNameExt`  
 Behandelt Namen als Pfade und wendet eine filename. ext-namens Übereinstimmung an.  
  
 `nsfRegularExpression`  
 Wendet eine namens Übereinstimmung unter Berücksichtigung der Groß-/Kleinschreibung mithilfe von Sternchen (*) und Fragezeichen (?) als Platzhalter an.  
  
 `nsfUndecoratedName`  
 Gilt nur für Symbole mit nicht ergänzten und ergänzten Namen.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Werte aus dieser Enumeration werden an die folgenden Methoden übermittelt:  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Anforderungen  
 Header: dia2.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession:: FindFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
