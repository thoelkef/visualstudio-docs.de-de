---
title: 'Idiasession:: Findlines | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 087248b4d4f25847fa8896a6896c335e2751b906
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910744"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Zeilennummern im angegebenen Kompiliereinheit und befehlsquellenbezeichner-Datei ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT findLines (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `compiland`  
 [in] Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das der Kompiliereinheit darstellt. Verwenden Sie diese Schnittstelle als einem Kontext, in dem für die Zeilennummern gesucht werden soll.  
  
 `file`  
 [in] Ein [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) Objekt, das die Quelldatei in die Suche nach den Zeilennummern darstellt.  
  
 `ppResult`  
 [out] Gibt eine [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) -Objekt, das eine Liste mit den Zeilennummern enthält abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



