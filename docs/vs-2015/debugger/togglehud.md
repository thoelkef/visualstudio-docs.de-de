---
title: ToggleHUD | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87c2571926b92e59ae03e5e988bbf535474dc6d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144576"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Schaltet die *HUD*-Überlagerung (Head-Up Display) der Grafikdiagnose ein oder aus.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Hinweise  
 Das Grafikdiagnose-HUD wird in der linken oberen Ecke der App angezeigt, die unter der Grafikdiagnose ausgeführt wird. Es werden Laufzeitinformationen zur App und zur Erfassung von Grafikinformationen sowie Meldungen angezeigt, die durch Aufrufen der Memberfunktion [AddMessage](../debugger/addmessage.md) hinzugefügt werden.  
  
 Um das HUD ein- und auszuschalten, müssen Sie Grafikinformationen nicht aktiv aufzeichnen – d.h. es kann durch eine Instanz der `VsgDbg`-Klasse ein- und ausgeschaltet werden, aber die Memberfunktion [Init](../debugger/init.md) muss nicht zuerst aufgerufen werden.
