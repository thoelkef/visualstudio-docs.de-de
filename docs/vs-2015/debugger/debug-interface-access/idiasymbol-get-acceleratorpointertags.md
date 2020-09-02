---
title: 'Idiasymmetribol:: get_acceleratorPointerTags | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 829c7a0193ce2742959f677e95dd4a499997cf5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149839"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt alle Accelerator-Zeiger-Tagwerte zurück, die einer C++ amp Accelerator-stubfunktion entsprechen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cnt`  
 in Die Größe des Ausgabe Arrays `pPointerTags` .  
  
 `pcnt`  
 vorgenommen Die Anzahl von Zugriffstasten-Zeiger Tags in der C++ amp Accelerator-Stub-Funktion.  
  
 `pPointerTags`  
 vorgenommen Ein `DWORD` Array Zeiger, der mit den Zugriffstasten-Tagwerten in der C++ amp Accelerator-Stub-Funktion gefüllt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode wird für eine `IDiaSymbol` Schnittstelle aufgerufen, die einer C++ amp Accelerator-stubfunktion entspricht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
