---
title: 'Idiaenumsectioncontrisb:: Item | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 06a82fbb52ccdf0f9fb9fda50a74f2cfb30e7648
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190005"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft Abschnitts Beiträge mithilfe eines Indexes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 Index  
 in Der Index des abzurufenden [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) -Objekts. Der Index liegt zwischen 0 und `count` -1, wobei `count` von der [idiaenumsectioncontrisb:: get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) -Methode zurückgegeben wird.  
  
 section  
 vorgenommen Gibt ein [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) -Objekt zurück, das den gewünschten Abschnitts Beitrag darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idiaenumsectioncontrisb:: get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
