---
title: ToggleHUD | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b224fdbd4dfadc6af29a0491bba5a18089c260b4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512055"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [ToggleHUD](https://docs.microsoft.com/visualstudio/debugger/graphics/togglehud).  
  
Schaltet die Grafikdiagnose *HUD* (Head-Up-Display) ein- oder ausschalten zu überlagern.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Hinweise  
 Das Grafikdiagnose-HUD wird in der linken oberen Ecke der App angezeigt, die unter der Grafikdiagnose ausgeführt wird. Es zeigt Laufzeitinformationen über die app und zur Erfassung von Grafikinformationen sowie Meldungen, die durch den Aufruf hinzugefügt werden die [AddMessage](../debugger/addmessage.md) Member-Funktion.  
  
 Um das HUD ein-oder auszuschalten, müssen Sie nicht aktiv Grafikinformationen aufzeichnen – d. h. es kann ein-/ausgeschaltet werden durch eine Instanz der der `VsgDbg` -Klasse, aber die [Init](../debugger/init.md) Memberfunktion nicht zuerst aufgerufen werden.



