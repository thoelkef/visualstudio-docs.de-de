---
title: ToggleHUD | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e49066d4625990119159ea72f59a3a3fe59d581c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953301"
---
# <a name="togglehud"></a>ToggleHUD
Schaltet die *HUD*-Überlagerung (Head-Up Display) der Grafikdiagnose ein oder aus.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Hinweise  
 Das Grafikdiagnose-HUD wird in der linken oberen Ecke der App angezeigt, die unter der Grafikdiagnose ausgeführt wird. Es zeigt Laufzeitinformationen über die app und zur Erfassung von Grafikinformationen sowie Meldungen, die durch den Aufruf hinzugefügt werden die [AddMessage](addmessage.md) Member-Funktion.  
  
 Um das HUD ein- und auszuschalten, müssen Sie Grafikinformationen nicht aktiv aufzeichnen – d.h. es kann durch eine Instanz der `VsgDbg`-Klasse ein- und ausgeschaltet werden, aber die Memberfunktion [Init](init.md) muss nicht zuerst aufgerufen werden.