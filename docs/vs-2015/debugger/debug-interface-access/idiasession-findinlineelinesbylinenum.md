---
title: 'IDiaSession:: findinlineelinesbylinenum | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d16bc6f3e2e8f190e3a26023407237509984cece
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841026"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft eine Enumeration ab, mit der ein Client die Zeilennummern Informationen aller Funktionen, die direkt oder indirekt in der angegebenen Quelldatei und Zeilennummer Inline sind, durchlaufen kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das die Kompilierungen darstellt, in der nach den Zeilennummern gesucht werden soll. Dieser Parameter darf nicht `NULL` sein.  
  
 `file`  
 in Ein [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) -Objekt, das die Quelldatei darstellt, in der gesucht werden soll. Dieser Parameter darf nicht `NULL` sein.  
  
 `linenum`  
 in Gibt eine einzeilige Zeilennummer an.  
  
> [!NOTE]
> Sie können keine NULL-Werte verwenden, um alle Zeilen anzugeben (verwenden Sie die [IDiaSession:: findLines](../../debugger/debug-interface-access/idiasession-findlines.md) -Methode, um alle Zeilen zu finden).  
  
 `column`  
 in Gibt die Spaltennummer an. Verwenden Sie 0 (null), um alle Spalten anzugeben. Eine Spalte ist ein Byte Offset in eine Zeile.  
  
 `ppResult`  
 vorgenommen Gibt ein [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) -Objekt zurück, das eine Liste der abgerufenen Zeilennummern enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
