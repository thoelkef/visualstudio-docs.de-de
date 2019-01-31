---
title: IDiaSession::findInlineeLinesByLinenum | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 432c0859041740c74e6c3264c318d46352d262b3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972692"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
Ruft eine Enumeration, die ermöglicht einem Client die Zeilennummerninformationen aller Funktionen durchlaufen, die inline erweitert wird, direkt oder indirekt in die angegebene Quelle Quelldatei- und Zeileninformationen Anzahl ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `compiland`  
 [in] Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das der Kompiliereinheit in die Suche nach den Zeilennummern darstellt. Dieser Parameter darf nicht sein `NULL`.  
  
 `file`  
 [in] Ein [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) Objekt, das die Quelldatei für die Suche darstellt. Dieser Parameter darf nicht sein `NULL`.  
  
 `linenum`  
 [in] Gibt eine 1-basierte Zeilennummer an.  
  
> [!NOTE]
>  Sie darf nicht 0 (null) verwenden, um alle Zeilen angeben (verwenden Sie die [idiasession:: Findlines](../../debugger/debug-interface-access/idiasession-findlines.md) Methode, um alle Zeilen zu ermitteln).  
  
 `column`  
 [in] Gibt die Nummer der Spalte an. Verwenden Sie 0 (null), um alle Spalten anzugeben. Eine Spalte ist ein Byteoffset in einer Zeile.  
  
 `ppResult`  
 [out] Gibt eine [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) Objekt, das eine Liste neben den Zeilennummern enthält, die abgerufen wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)