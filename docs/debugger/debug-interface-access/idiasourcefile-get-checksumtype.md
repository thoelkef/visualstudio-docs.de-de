---
title: 'Idiasourcefile:: Get_checksumtype | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 39fa53d00d17446e63170d5b729d2e669ecb987b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948420"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
Ruft den Typ von Prüfsumme ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Prüfsumme-Typ zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Checksum-Typ ist ein Wert, der eine Prüfsumme der Prüfsummenalgorithmus zugeordnet werden kann. Beispielsweise kann das Standardformat der PDB-Datei in der Regel einen der folgenden Werte aufweisen:  
  
|Typ von Prüfsumme an|CryptoAPI-Bezeichnung|Beschreibung|  
|-------------------|---------------------|-----------------|  
|0|\<Keine >|Keine Prüfsumme vorhanden ist.|  
|1|`CALG_MD5`|Prüfsumme, die mit dem MD5-Hash-Algorithmus generiert.|  
|2|`CALG_SHA1`|Prüfsumme, die mit dem SHA1-Hashalgorithmus generiert werden.|  
  
 Die `CryptoAPI` Bezeichnungen sind von der `ALG_ID` Enumeration. Weitere Informationen zu Hashalgorithmen, finden Sie in der `CryptoAPI` der Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Rufen Sie zum Abrufen der tatsächlichen Prüfsumme Bytes für die Quelldatei der [idiasourcefile:: Get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)