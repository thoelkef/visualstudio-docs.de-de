---
title: 'IDiaEnumLineNumbers:: Clone | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Clone method
ms.assetid: fcd2479a-8ff7-4aba-a737-06123c280d54
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 21b1a47f46765c9f7bf2d1832ff54bf50c5f59a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185494"
---
# <a name="idiaenumlinenumbersclone"></a>IDiaEnumLineNumbers::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumLineNumbers** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppenum`  
 vorgenommen Gibt ein [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) -Objekt zurück, das ein Duplikat des Enumerators enthält. Die Zeilennummern werden nicht dupliziert, sondern nur der Enumerator.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
