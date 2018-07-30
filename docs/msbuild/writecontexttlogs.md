---
title: WriteContextTLogs | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a01dbd11411204affa082bfa0772530662657853
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230798"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
Schreibt Protokolldateien für den aktuellen Kontext  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Parameter  
 [in] `intermediateDirectory`  
 Das Verzeichnis, in dem das Nachverfolgungsprotokoll gespeichert werden soll  
  
 [in] `tlogRootName`  
 Der Stammname des Namens der Protoktolldatei  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn der Nachverfolgungskontext erstellt wurde  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** *FileTracker.h*  
  
## <a name="see-also"></a>Siehe auch  
 [WriteAllTLogs](../msbuild/writealltlogs.md)