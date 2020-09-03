---
title: IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14c9924346471e098d9ba9f1abb52fda0d3c9969
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198670"
---
# <a name="idiaaddressmapput_relativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ermöglicht dem Client, die Berechnung und Verwendung von relativen virtuellen Adressen (RVA) zu aktivieren oder zu deaktivieren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 NewVal  
 in Legen Sie auf fest `TRUE` , um zu aktivieren oder `FALSE` zu deaktivieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Adressen für Debug-Objekte, die von Dia-Schnittstellen und relativ zur Image Basis der ausführbaren Datei beschrieben werden, können als relative virtuelle Adressen abgerufen werden.  
  
 Die Verwendung von RVAs wird aktiviert, wenn Segmente anfänglich aus einer PDB-Datei geladen werden. Um den aktuellen Status der Verwendung von RVAs abzurufen, müssen Sie die [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) -Methode abrufen.  
  
 Die- `put_relativeVirtualAddress` Methode muss aufgerufen werden, um RVAs zu aktivieren, nachdem ein erfolgreicher Aufruf der [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) -Methode neue Bild Header erstellt hat.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
