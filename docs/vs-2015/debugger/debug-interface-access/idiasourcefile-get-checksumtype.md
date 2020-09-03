---
title: 'IDiaSourceFile:: get_checksumType | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f859bce63e2976b23ab613e249dad41b2bc63486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190701"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Prüfsummen Datentyp ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt den Prüfsummen Datentyp zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Prüfsumme-Typ ist ein Wert, der einem Prüfsummen Algorithmus zugeordnet werden kann. Beispielsweise kann das standardmäßige PDB-Dateiformat einen der folgenden Werte aufweisen:  
  
|Prüfsummen-Typ|Kryptoapi-Bezeichnung|Beschreibung|  
|-------------------|---------------------|-----------------|  
|0|\<none>|Keine Prüfsumme vorhanden.|  
|1|`CALG_MD5`|mit dem MD5-Hash Algorithmus generierte Prüfsumme.|  
|2|`CALG_SHA1`|mit dem SHA1-Hash Algorithmus generierte Prüfsumme.|  
  
 Die `CryptoAPI` Bezeichnungen stammen aus der- `ALG_ID` Enumeration. Weitere Informationen zu Hash Algorithmen finden Sie im `CryptoAPI` Abschnitt von Microsoft [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] .  
  
 Rufen Sie die [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) -Methode auf, um die tatsächlichen Prüfsummen Bytes für die Quelldatei abzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)
