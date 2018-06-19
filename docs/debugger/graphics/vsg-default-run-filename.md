---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 303bce554ff6345a37719a8d2f529f3c1ffe02e2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472013"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
Definiert den Standarddateinamen der Grafikprotokolldatei.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Parameter  
 `filename`  
 Der Dateiname, der der Grafikprotokolldatei standardmäßig zugewiesen wird, wenn Grafikinformationen programmgesteuert erfasst werden.  
  
## <a name="value"></a>Wert  
 Ein Zeichenfolgenliteral, das den Dateinamen der Grafikprotokolldatei darstellt. Standardmäßig ist dies L"default.vsglog".  
  
```C++  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Hinweise  
 Wenn das Präprozessorsymbol `DONT_SAVE_VSGLOG_TO_TEMP` definiert ist, ist der Dateiname relativ zum aktuellen Verzeichnis der aufgezeichneten App oder ein absoluter Pfad. Andernfalls ist er relativ zum Verzeichnis der temporären Dateien des Benutzers und kann kein absoluter Pfad sein.  
  
 Um den definierten Dateinamen zu ändern, Sie müssen ihn erneut definieren, bevor Sie einschließen `vsgcapture.h` im Programm.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie der Standarddateiname der Erfassungsdatei geändert wird:  
  
```C++  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)