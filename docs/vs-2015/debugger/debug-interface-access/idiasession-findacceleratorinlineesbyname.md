---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47883395ec12cac60d3a21651432f5ac21cc64a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151750"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt eine Enumeration von Symbolen für Inline Frames zurück, die dem angegebenen Inline Funktionsnamen entsprechen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `name`  
 in Der Name der inlinees-Funktion, die durchsucht werden soll.  
  
 `option`  
 in Die namens Suchoptionen, die beim Suchen nach Inline Frames verwendet werden sollen, die entsprechen `name` . Weitere Informationen finden Sie unter [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 vorgenommen Ein Zeiger auf einen `IDiaEnumSymbols` Schnittstellen Zeiger, der mit dem Ergebnis initialisiert wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion sucht inlinees zuzuordnen sind nur innerhalb von Accelerator-Stub-Funktionen. Systemeigene C++-Prozedur Datensätze werden ignoriert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
