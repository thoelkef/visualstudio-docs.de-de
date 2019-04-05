---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2980d34028c58a6abadb2df21bf22c8d37cda6e0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946513"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiert den Standarddateinamen der Grafikprotokolldatei.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Parameter  
 `filename`  
 Der Dateiname, der der Grafikprotokolldatei standardmäßig zugewiesen wird, wenn Grafikinformationen programmgesteuert erfasst werden.  
  
## <a name="value"></a>Wert  
 Ein Zeichenfolgenliteral, das den Dateinamen der Grafikprotokolldatei darstellt. Standardmäßig ist dies L"default.vsglog".  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Hinweise  
 Wenn das Präprozessorsymbol `DONT_SAVE_VSGLOG_TO_TEMP` definiert ist, ist der Dateiname relativ zum aktuellen Verzeichnis der aufgezeichneten App oder ein absoluter Pfad. Andernfalls ist er relativ zum Verzeichnis der temporären Dateien des Benutzers und kann kein absoluter Pfad sein.  
  
 Um den definierten Dateinamen zu ändern, müssen Sie neu definieren sie bevor Sie einfügen `vsgcapture.h` in Ihrem Programm.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie der Standarddateiname der Erfassungsdatei geändert wird:  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)
