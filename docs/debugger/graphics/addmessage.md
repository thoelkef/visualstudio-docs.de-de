---
title: AddMessage | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6555072bcbebe24011ca0701f02f48bc1703c34a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985734"
---
# <a name="addmessage"></a>AddMessage
Fügt dem Grafikdiagnose-*HUD* (Head-Up Display) eine benutzerdefinierte Meldung hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `szMessage`  
 Die dem HUD hinzuzufügende Meldung.  
  
## <a name="remarks"></a>Hinweise  
 Das Grafikdiagnose-HUD wird in der linken oberen Ecke der App angezeigt, die unter der Grafikdiagnose ausgeführt wird. Es werden Laufzeitinformationen über die App und die Erfassung von Grafikinformationen sowie Meldungen angezeigt, die hinzugefügt werden, indem diese Funktion aufgerufen wird.  
  
 Um dem HUD eine Meldung hinzuzufügen, müssen Sie Grafikinformationen nicht aktiv erfassen – d.h. eine Meldung kann durch eine Instanz der `VsgDbg`-Klasse hinzugefügt werden, die Memberfunktion [Init](init.md) muss jedoch nicht zuerst aufgerufen werden. Meldungen werden nur im HUD angezeigt, sie werden nicht in der Grafikprotokolldatei aufgezeichnet.