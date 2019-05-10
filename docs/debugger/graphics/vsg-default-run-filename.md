---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb56f7ef08241aed2e109e6845af8fb596cb42e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895382"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
Definiert den Standarddateinamen der Grafikprotokolldatei.

## <a name="syntax"></a>Syntax

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Parameter
 `filename` Der Dateiname, der der Grafikprotokolldatei standardmäßig zugewiesen wird, wenn Grafikinformationen programmgesteuert erfasst werden.

## <a name="value"></a>Wert
 Ein Zeichenfolgenliteral, das den Dateinamen der Grafikprotokolldatei darstellt. Standardmäßig ist dies L"default.vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Hinweise
 Wenn das Präprozessorsymbol `DONT_SAVE_VSGLOG_TO_TEMP` definiert ist, ist der Dateiname relativ zum aktuellen Verzeichnis der aufgezeichneten App oder ein absoluter Pfad. Andernfalls ist er relativ zum Verzeichnis der temporären Dateien des Benutzers und kann kein absoluter Pfad sein.

 Um den definierten Dateinamen zu ändern, müssen Sie neu definieren sie bevor Sie einfügen `vsgcapture.h` in Ihrem Programm.

## <a name="example"></a>Beispiel
 Dieses Beispiel zeigt, wie der Standarddateiname der Erfassungsdatei geändert wird:

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Siehe auch
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)