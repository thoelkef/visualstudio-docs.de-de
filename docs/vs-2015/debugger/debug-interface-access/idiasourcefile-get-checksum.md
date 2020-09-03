---
title: 'IDiaSourceFile:: get_checksum | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f87f5cdd937c0e172e7b96cf0858423b14686d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190736"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Prüfsumme Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cbData`  
 in Größe des Daten Puffers in Bytes.  
  
 `pcbData`  
 vorgenommen Gibt die Anzahl der Prüfsummen Bytes zurück. Dieser Parameter darf nicht `NULL` sein.  
  
 `data`  
 [in, out] Ein Puffer, der mit der Prüfsumme Bytes gefüllt ist. Wenn dieser Parameter ist `NULL` , dann wird `pcbData` die erforderliche Anzahl von Bytes zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Um den Typ des Prüfsummen Algorithmus zu ermitteln, der zum Generieren der Prüfsummen Bytes verwendet wurde, rufen Sie die [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) -Methode auf.  
  
 Die Prüfsumme wird in der Regel aus dem Image der Quelldatei generiert, sodass sich Änderungen in der Quelldatei in Änderungen der Prüfsummen Bytes widerspiegeln. Wenn die Prüfsummen Bytes nicht mit einer Prüfsumme identisch sind, die aus dem geladenen Bild der Datei generiert wurde, sollte die Datei als beschädigt oder manipuliert angesehen werden.  
  
 Typische Prüfsummen sind nie mehr als 32 Bytes groß, gehen jedoch nicht davon aus, dass es sich um die maximale Größe einer Prüfsumme handelt. Legen Sie den- `data` Parameter auf fest `NULL` , um die Anzahl der Bytes abzurufen, die zum Abrufen der Prüfsumme benötigt werden. Weisen Sie dann einen Puffer mit der entsprechenden Größe zu, und nennen Sie diese Methode mit dem neuen Puffer.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)
