---
title: ToggleHUD | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: baaa776a64d9b778c161ab7e65bb0f15e6c90099
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="togglehud"></a>ToggleHUD
Schaltet die Grafikdiagnose *HUD* (Head-Up-Display) überlagern, ein- oder ausschalten.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Hinweise  
 Das Grafikdiagnose-HUD wird in der linken oberen Ecke der App angezeigt, die unter der Grafikdiagnose ausgeführt wird. Es zeigt Laufzeitinformationen über die app und zur Erfassung von Grafikinformationen sowie Meldungen, die durch den Aufruf hinzugefügt werden die [AddMessage](addmessage.md) Memberfunktion.  
  
 Um die HUD ein-oder auszuschalten, müssen Sie nicht aktiv Grafikinformationen erfasst werden – d. h., es kann ein-/ausgeschaltet werden durch eine Instanz von der `VsgDbg` -Klasse, aber die [Init](init.md) keinen Member-Funktion zuerst aufgerufen werden.