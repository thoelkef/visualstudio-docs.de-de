---
title: 'Idiasymmetribol:: get_lexicalParent | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lexicalParent method
ms.assetid: 4d119965-33a8-474c-9c64-95c5218c389c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b5f9da456282daca52d6c924b62f21e13545928
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841088"
---
# <a name="idiasymbolget_lexicalparent"></a>IDiaSymbol::get_lexicalParent
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft einen Verweis auf das lexikalische übergeordnete Element des Symbols ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_lexicalParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt zurück, das das lexikalische Element des Symbols darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der- `S_FALSE` oder-Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Das lexikalische Element eines Symbols ist die einschließende Funktion oder das einschließende Modul. Beispielsweise handelt es sich bei dem lexikalischen übergeordneten Element eines Funktions Parameters oder einer lokalen Variablen um die Funktion selbst, während das lexikalische Element der Funktion das Modul ist, in dem es definiert ist.  
  
 Die möglichen Symbole, die als lexikalische übergeordnete Elemente angezeigt werden können, sind in [der lexikalischen Hierarchie von Symbol Typen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)dokumentiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
