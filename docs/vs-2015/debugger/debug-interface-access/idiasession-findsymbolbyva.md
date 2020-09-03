---
title: 'IDiaSession:: findSymbolByVA | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByVA method
ms.assetid: 0350df23-9a5d-4e8d-8c26-7f571d8fb1af
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dfc2e34b2e75bf81a47a02c4f6048f8be8a64fcc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190800"
---
# <a name="idiasessionfindsymbolbyva"></a>IDiaSession::findSymbolByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft einen angegebenen Symboltyp ab, der eine angegebene virtuelle Adresse enthält bzw. am nächsten liegt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT findSymbolByVA (   
   ULONGLONG    va,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `va`  
 in Gibt die virtuelle Adresse an.  
  
 `symtag`  
 in Symboltyp, der gefunden werden soll. Werte werden aus der Enumeration der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) entnommen.  
  
 `ppSymbol`  
 vorgenommen Gibt ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt zurück, das das abgerufene Symbol darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByVA( va, SymTagFunction, &pFunc );  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
