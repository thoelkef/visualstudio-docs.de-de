---
title: 'Idiasourcefile:: Get_checksumtype | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7f34e840dc6389b721610251c592480afbdda5f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
 [out] Gibt den Typ von Prüfsumme an.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Typ von Prüfsumme wird ein Wert, der eine Prüfsummenalgorithmus zugeordnet werden kann. Beispielsweise kann das Standardformat der PDB-Datei in der Regel einen der folgenden Werte aufweisen:  
  
|Typ von Prüfsumme an|CryptoAPI-Bezeichnung|Beschreibung|  
|-------------------|---------------------|-----------------|  
|0|\<keine >|Keine Prüfsumme vorhanden ist.|  
|1|`CALG_MD5`|die Prüfsumme mit MD5-Hashalgorithmus generiert.|  
|2|`CALG_SHA1`|die Prüfsumme mit SHA1-Hashalgorithmus generiert.|  
  
 Die `CryptoAPI` Bezeichnungen sind von der `ALG_ID` Enumeration. Weitere Informationen zu Hashalgorithmen, wenden Sie sich an den `CryptoAPI` der Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Um die tatsächliche Prüfsumme Bytes für die Quelldatei zu erhalten, rufen Sie die [idiasourcefile:: Get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)