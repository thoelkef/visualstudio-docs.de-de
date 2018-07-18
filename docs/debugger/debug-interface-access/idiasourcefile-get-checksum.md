---
title: 'Idiasourcefile:: Get_checksum | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 002ad16d94467c135e08ef0040fd7ffd51462719
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31463136"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
Ruft die Prüfsumme Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cbData`  
 [in] Die Größe des Datenpuffers in Bytes.  
  
 `pcbData`  
 [out] Gibt die Anzahl der Prüfsumme Bytes zurück. Dieser Parameter darf nicht sein `NULL`.  
  
 `data`  
 [in, out] Ein Puffer, der mit der Prüfsumme Bytes gefüllt ist. Wenn dieser Parameter ist `NULL`, klicken Sie dann `pcbData` gibt die Anzahl der Bytes, die erforderlich sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Um den Typ des Prüfsummenalgorithmus zu ermitteln, mit denen die Prüfsumme Bytes generiert wurde, rufen die [idiasourcefile:: Get_checksumtype](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) Methode.  
  
 Die Prüfsumme wird in der Regel aus dem Image der Quelldatei generiert, damit die Änderungen in der Quelldatei zu Änderungen in den Bytes Prüfsumme wiedergegeben werden. Die Prüfsumme Bytes stimmen nicht überein. wird eine Prüfsumme aus dem geladenen Image der Datei generiert wird, und klicken Sie dann die Datei berücksichtigt werden sollten beschädigt oder manipuliert.  
  
 Typische Prüfsummen nie mehr als 32 Bytes groß sind jedoch nicht davon ausgehen, dass die maximale Größe der Prüfsumme ist. Legen Sie die `data` Parameter `NULL` beim Abrufen der Anzahl von Bytes erforderlich, um die Prüfsumme abzurufen. Klicken Sie dann zuordnen Sie einen Puffer der entsprechenden Größe zu, und rufen Sie diese Methode einmal mit dem neuen Puffer.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)