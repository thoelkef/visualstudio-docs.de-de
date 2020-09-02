---
title: 'Idiasymmetribol:: findsymbolsbyrvaforacceleratorpointertag | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee1aea023124fb8277fd13cf341a63fca92c37cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149862"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn ein entsprechender Tagwert angegeben ist, gibt diese Methode eine Enumeration von Symbolen zurück, die in dieser stubfunktion an einer angegebenen relativen virtuellen Adresse enthalten sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>Parameter  
 `tagValue`  
 in Der zeigertag Wert, für den die pointee-Symbol Datensätze gefunden werden.  
  
 `rva`  
 in Die RVA, mit der die Symbole gefiltert werden, die der pointee-Variablen mit dem angegebenen Tagwert entsprechen.  
  
 `ppResult`  
 vorgenommen Ein Zeiger auf einen `IDiaEnumSymbols` Schnittstellen Zeiger, der mit dem Ergebnis initialisiert wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode wird nur für eine `IDiaSymbol` Schnittstelle aufgerufen, die einer Zugriffstasten-Stub-Funktion entspricht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
