---
title: IDiaSession::findInlineeLinesByLinenum | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ecd508c98a8a40ea6f89b4d2054326c5794af6a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515189"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDiaSession::findInlineeLinesByLinenum](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-findinlineelinesbylinenum).  
  
Ruft eine Enumeration, die ermöglicht einem Client die Zeilennummerninformationen aller Funktionen durchlaufen, die inline erweitert wird, direkt oder indirekt in die angegebene Quelle Quelldatei- und Zeileninformationen Anzahl ab.  
  
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



