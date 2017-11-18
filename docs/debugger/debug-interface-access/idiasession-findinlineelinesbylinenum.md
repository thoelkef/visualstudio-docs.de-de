---
title: IDiaSession::findInlineeLinesByLinenum | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c18b2919605e3b2de6f59303c304ffb3d8f05198
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
Ruft eine Enumeration, die ermöglicht einem Client zum iterieren durch die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt in die angegebene Quelle und die Zeilennummer der Anzahl ab.  
  
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
 [in] Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das der Kompiliereinheit zu durchsuchende für die Zeilennummern darstellt. Dieser Parameter darf nicht sein `NULL`.  
  
 `file`  
 [in] Ein [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) -Objekt, das die Quelldatei, in dem gesucht werden soll. Dieser Parameter darf nicht sein `NULL`.  
  
 `linenum`  
 [in] Gibt eine Zeile eins an.  
  
> [!NOTE]
>  Sie können nicht 0 (null) verwenden, um alle Zeilen angeben (verwenden Sie die [idiasession:: Findlines](../../debugger/debug-interface-access/idiasession-findlines.md) Methode, um alle Zeilen zu suchen).  
  
 `column`  
 [in] Gibt die Nummer der Spalte an. Verwenden Sie 0 (null), um alle Spalten anzugeben. Eine Spalte ist ein Byte-Offset in einer Zeile.  
  
 `ppResult`  
 [out] Gibt eine [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) -Objekt, das eine Liste mit den Zeilennummern enthält, die abgerufen wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)