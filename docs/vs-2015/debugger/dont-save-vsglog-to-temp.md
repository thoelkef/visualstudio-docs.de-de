---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 449c6c1ecdb0644b9b52b6ec12ce867dc34d66c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156106"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiert durch das Vorhandensein, ob die Grafikprotokolldatei im Verzeichnis der temporären Dateien des Benutzers gespeichert wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Wert  
 Ein Präprozessorsymbol, das durch sein Vorhandensein bzw. seine Abwesenheit bestimmt, ob die Grafikprotokolldatei im Verzeichnis der temporären Dateien des Benutzers gespeichert wird. Wenn dieses Symbol definiert wird, ist der Dateiname, der durch `VSG_DEFAULT_RUN_FILENAME` definiert ist, relativ zum aktuellen Verzeichnis der erfassten App oder ein absoluter Pfad. Andernfalls ist der Dateiname, der durch `VSG_DEFAULT_RUN_FILENAME` definiert ist, relativ zum Verzeichnis der temporären Dateien des Benutzers und kann kein absoluter Pfad sein.  
  
## <a name="remarks"></a>Hinweise  
 Abhängig von den Berechtigungen des Benutzers kann die Grafikprotokolldatei möglicherweise nicht an einem beliebigen Speicherort gespeichert werden. Es wird empfohlen, Grafikprotokolle vorzugsweise im Verzeichnis der temporären Dateien des Benutzers oder an einem anderen, als funktionierend bekannten Speicherort zu speichern, wenn Sie unsicher sind, ob in den Speicherort, den Sie auswählen würden, vom Benutzer geschrieben werden kann.  
  
 Um zu verhindern, dass die Grafikprotokolldatei im Verzeichnis der temporären Dateien gespeichert wird, müssen Sie `DONT_SAVE_VSGLOG_TO_TEMP` definieren, bevor Sie `vsgcapture.h` einschließen.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie Sie die Grafikprotokolldatei in einem absoluten Pfad auf dem Hostcomputer speichern können.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
