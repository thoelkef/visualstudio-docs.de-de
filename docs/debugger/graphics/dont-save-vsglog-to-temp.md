---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5a98081aa73d11d9a2edea9293804d6c83a211d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Definiert durch das Vorhandensein, ob die Grafikprotokolldatei im Verzeichnis der temporären Dateien des Benutzers gespeichert wird.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Wert  
 Ein Präprozessorsymbol, das durch sein Vorhandensein bzw. seine Abwesenheit bestimmt, ob die Grafikprotokolldatei im Verzeichnis der temporären Dateien des Benutzers gespeichert wird. Wenn dieses Symbol definiert wird, ist der Dateiname, der durch `VSG_DEFAULT_RUN_FILENAME` definiert ist, relativ zum aktuellen Verzeichnis der erfassten App oder ein absoluter Pfad. Andernfalls ist der Dateiname, der durch `VSG_DEFAULT_RUN_FILENAME` definiert ist, relativ zum Verzeichnis der temporären Dateien des Benutzers und kann kein absoluter Pfad sein.  
  
## <a name="remarks"></a>Hinweise  
 Abhängig von den Berechtigungen des Benutzers kann die Grafikprotokolldatei möglicherweise nicht an einem beliebigen Speicherort gespeichert werden. Es wird empfohlen, Grafikprotokolle vorzugsweise im Verzeichnis der temporären Dateien des Benutzers oder an einem anderen, als funktionierend bekannten Speicherort zu speichern, wenn Sie unsicher sind, ob in den Speicherort, den Sie auswählen würden, vom Benutzer geschrieben werden kann.  
  
 Um zu verhindern, dass die grafikprotokolldatei an das Verzeichnis für temporäre Dateien gespeichert werden, müssen Sie definieren `DONT_SAVE_VSGLOG_TO_TEMP` bevor Sie einfügen `vsgcapture.h`.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie Sie die Grafikprotokolldatei in einem absoluten Pfad auf dem Hostcomputer speichern können.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)