---
title: 'Idiasymmetribol:: get_liveRangeStartAddressSection | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df3faba1309b5a26316b615042492f96b9401a01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840931"
---
# <a name="idiasymbolget_liverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt den Abschnitts Teil der Startadresse des Bereichs zurück, in dem das lokale Symbol gültig ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_liveRangeStartAddressSection (   
   DWORD* section  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `section`  
 vorgenommen Gibt den Abschnitts Teil des Start Adress Bereichs zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Ein zurückgegebener Fehlercode bedeutet, dass das Symbol keine Informationen zum Live Bereich enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Die durch den Abschnitt und den Offset gebildete Adresse ist der Anfang des Bereichs, in dem das Symbol gültig ist.  
  
 Um den Offset Teil der Adresse zu erhalten, verwenden Sie [idiasymmetribol:: get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
