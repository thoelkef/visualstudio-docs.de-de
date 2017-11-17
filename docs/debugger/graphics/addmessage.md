---
title: AddMessage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0050f5022b31020879b45e45da48546e5a7caa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="addmessage"></a>AddMessage
Fügt eine benutzerdefinierte Meldung an das Grafikdiagnose *HUD* (Head-Up-Display).  
  
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
  
 Um die HUD eine Meldung hinzugefügt haben, müssen Sie nicht aktiv Grafikinformationen erfasst werden – d. h. eine Nachricht über eine Instanz hinzugefügt werden kann die `VsgDbg` -Klasse, aber die [Init](init.md) Member-Funktion werden keine zuerst aufgerufen werden. Meldungen werden nur im HUD angezeigt, sie werden nicht in der Grafikprotokolldatei aufgezeichnet.