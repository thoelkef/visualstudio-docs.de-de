---
title: ToggleHUD | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 62d202bfca33619c14d00ec99dc44857cb01bb6a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250445"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Schaltet die Grafikdiagnose *HUD* (Head-Up-Display) ein- oder ausschalten zu überlagern.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Hinweise  
 Das Grafikdiagnose-HUD wird in der linken oberen Ecke der App angezeigt, die unter der Grafikdiagnose ausgeführt wird. Es zeigt Laufzeitinformationen über die app und zur Erfassung von Grafikinformationen sowie Meldungen, die durch den Aufruf hinzugefügt werden die [AddMessage](../debugger/addmessage.md) Member-Funktion.  
  
 Um das HUD ein-oder auszuschalten, müssen Sie nicht aktiv Grafikinformationen aufzeichnen – d. h. es kann ein-/ausgeschaltet werden durch eine Instanz der der `VsgDbg` -Klasse, aber die [Init](../debugger/init.md) Memberfunktion nicht zuerst aufgerufen werden.



