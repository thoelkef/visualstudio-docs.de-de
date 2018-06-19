---
title: Kopieren (programmgesteuerte Aufzeichnung) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67b20a6032a073238f6eb3a8c157c96f95d5c67f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472093"
---
# <a name="copy-programmatic-capture"></a>Kopieren (Programmgesteuerte Aufzeichnung)
Kopiert den Inhalt der aktiven Grafikprotokolldatei (VSGLOG) in eine neue Datei.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `szNewVSGLog`  
 Der Dateiname der neuen Grafikprotokolldatei.  
  
## <a name="remarks"></a>Hinweise  
 Um die Grafikinformationen in eine neuen Datei zu kopieren, müssen Sie bereits einige Grafikinformationen erfasst haben, andernfalls geschieht nichts.