---
title: "IDiaSession::findInlineeLinesByLinenum | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineeLinesByLinenum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Funktionen direkt oder indirekt zu durchlaufen, die inline sind, in der Quelldatei angegebenen und der Zeilennummer.  
  
## Syntax  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parameter  
 `compiland`  
 \[in\] Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt, das die Kompiliereinheit darstellt, in der nach den Zeilennummern gesucht werden soll.  Dieser Parameter darf nicht `NULL` sein.  
  
 `file`  
 \[\] [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) in ein Objekt, das die Quelldatei darstellt, in der suchen.  Dieser Parameter darf nicht `NULL` sein.  
  
 `linenum`  
 \[in\] Gibt eine 1\-basierte Zeilennummer an.  
  
> [!NOTE]
>  Sie können 0 nicht verwenden, um alle Zeilen anzugeben \(verwenden Sie die [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)\-Methode, um alle Zeilen zu suchen\).  
  
 `column`  
 \[in\]Legt die Spaltennummer fest.  Verwenden Sie 0, um alle Spalten anzugeben.  Eine Spalte ist ein Byteoffset in eine Zeile.  
  
 `ppResult`  
 \[out\] [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) gibt ein Objekt zurück, das eine Liste der Zeilennummern enthält, die abgerufen wurden.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)